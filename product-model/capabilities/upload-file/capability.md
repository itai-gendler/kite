---
availability:
- place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/api/media.go#upload
- kind: code
  role: implementation
  target: internal/store/file/writer.go#putMedia
- kind: code
  role: implementation
  target: internal/api/media.go#receive
---

# Add a file to an item

Drop or choose pictures and other files in the editor, the cover field, an image field or the Files list. A post keeps them beside it in its folder, published with its address; a page, kept as a single file, puts them among the site's own uploads. An item never saved is saved first. A photo loses where it was taken before it is stored.
