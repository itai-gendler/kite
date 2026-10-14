---
availability:
- place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/api/write.go#handleDelete
- kind: code
  role: implementation
  target: internal/store/file/writer.go
---

# Delete an item

Move an item to the trash, from the editor or from a list, one or several at once. Its files and attachments stay on disk so it can be restored; the studio offers no way to delete it for good.
