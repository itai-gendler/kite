---
appliesTo:
- type: capability
  id: upload-file
- type: entity
  id: file
references:
- kind: code
  role: implementation
  target: internal/store/file/writer.go#putMedia
- kind: doc
  role: intent
  target: docs/reference.md
  title: Moving from Hugo
---

# A page's files are kept among the site's uploads, a post's beside it

A post kept as a folder keeps its files there and publishes them with its address; a page, or any item kept as a single file, has no folder, so its files go to static/uploads/ and are linked from the site's root.
