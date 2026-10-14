---
availability:
- place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/api/media.go#handleDeleteMedia
---

# Delete a file

Remove a file a post keeps from its folder, from the Files list; the studio warns when the text, the cover or a field still uses it.
