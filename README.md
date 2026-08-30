# MMD Spine Models

This repository stores Spine runtime assets used by the MMD HUD project.
Each model is kept as an immutable versioned package so a released HUD can
continue to use the same files after newer models are added.

## Layout

```text
models/<model-id>/<asset-version>/
  *.skel or *.json
  *.atlas
  atlas page textures (*.png)
  model.js
  model.json
```

The skeleton, atlas, and every texture referenced by the atlas must remain in
the same version directory. Do not rename an atlas page without updating the
atlas file.

`model.js` is a generated browser package containing the skeleton and atlas as
Base64 data. The MMD stage allows external scripts but restricts cross-origin
XHR, so HOST loads this file with a `<script src>` tag and loads atlas page
textures as images. Regenerate it after changing the Spine export:

```powershell
node scripts/build-spine-package.mjs
```

## Current model

`models/nikke-rupee-winter-shopper/1.0.0/` contains the local Rupee: Winter
Shopper binary skeleton and its atlas texture. The source is recorded in
`model.json`; verify that you have the right to redistribute any model before
publishing this repository publicly.

## CDN usage

After pushing this repository to a public GitHub repository and creating a
release tag, use a pinned jsDelivr URL. Replace the owner and repository name:

```text
https://cdn.jsdelivr.net/gh/<owner>/<repo>@v1.0.0/models/nikke-rupee-winter-shopper/1.0.0/c203_00.skel
```

Use the same base directory for the `.atlas` and `.png` files. Avoid `@main`
for production URLs because it is mutable and can be cached inconsistently.

## Adding a model

1. Create `models/<model-id>/<asset-version>/`.
2. Copy the complete Spine export package into that directory.
3. Add a `model.json` entry and update `catalog.json`.
4. Test the package in the HOST local preview.
5. Commit the files and create a new repository tag.

Do not overwrite an already published asset version. Spine export/runtime
compatibility is recorded in `model.json`.
