---
appliesTo:
- type: capability
  id: upload-file
  contexts:
  - place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/api/media.go#allowedMedia
---

# Only files of the kinds a site hosts, up to 32 MB each, are added

Pictures, audio, video, PDF, text, CSV, JSON and web fonts of the listed kinds are taken; anything else is refused.

## Rationale

What is uploaded is published with the site; an open list would make the site a place to host anything.
