# NIKKE HUD Asset Release v2

730 catalog entries and 1,756 model variants for the MMD HUD. Runtime versions: Spine 4.0 and 4.1.

- packages/: skeleton and atlas data registered by browser scripts, avoiding cross-origin XHR.
- thumbnails/: small static gallery previews; no model package is required to browse them.
- ../../models/nikke-db-2026-08-26/ and ../../models/nikke-spine-library/: referenced PNG textures.
- manifest.json: published paths, transfer sizes and SHA-256 hashes. No local workstation paths.

The original .skel and .atlas data is contained in each packages/*.js file as Base64.
Use the immutable v2.0.0 tag, not main, for production CDN URLs.
Model/source ownership remains with the respective rights holders. Runtime licenses are separate.
