---
availability:
- place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/api/media.go#handleReplaceMedia
---

# Replace a file

Put a new version of a file a post keeps in its place, under its name, from the Files list, so every link to it still reaches it.
