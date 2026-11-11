# Thumbnail Pool

This folder holds the operator's pre-made YouTube thumbnails that the Deal Drops / AI Unboxed pipeline rotates through automatically — no AI generation needed for these.

## How to use it

Upload exactly **10 JPG images** into each folder below, named `1.jpg` through `10.jpg`:

- `pool/nordvpn/1.jpg` ... `pool/nordvpn/10.jpg` — 10 NordVPN thumbnails
- `pool/helium10/1.jpg` ... `pool/helium10/10.jpg` — 10 Helium10 thumbnails

Recommended size: **1280x720** (16:9). If you upload a different size, the pipeline will auto-crop/resize it to fit.

## How it's used

Every time the automation renders and uploads a new video for a product, it fetches the next thumbnail in order (1 -> 2 -> 3 ... -> 10 -> back to 1) from this pool and sets it as that video's YouTube thumbnail. The rotation position is tracked automatically by the pipeline (via its `/state` key-value store) — you don't need to do anything beyond keeping all 10 slots filled.

If a slot isn't uploaded yet, the pipeline falls back to its old AI-generated thumbnail for that one video, so nothing breaks while you're still uploading the set.

## Replacing images later

Just overwrite the file at the same path (e.g. replace `pool/nordvpn/3.jpg` with a new image) — the pipeline always fetches the current content at that path, so changes take effect on the very next render that lands on that slot.
