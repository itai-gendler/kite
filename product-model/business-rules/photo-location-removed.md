---
appliesTo:
- type: capability
  id: upload-file
- type: capability
  id: replace-file
references:
- kind: code
  role: implementation
  target: internal/api/media.go#receive
---

# A photo added in the studio loses where it was taken

Before it is stored, a JPEG, PNG, WebP or AVIF loses the GPS of its EXIF and the place its XMP gives, in the previews some cameras keep inside it too; its pixels, orientation, camera and time stay, and the studio says when it took a place out. A file added with git is published as it is.

## Rationale

What is stored is published.
