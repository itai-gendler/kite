---
appliesTo:
- type: capability
  id: delete-item
- type: capability
  id: restore-item
references:
- kind: code
  role: implementation
  target: internal/store/file/writer.go
- kind: code
  role: implementation
  target: internal/api/write.go#handleDelete
---

# Deleting an item keeps it on disk

An item deleted in the studio goes to the trash with its files and attachments and can be restored with the status it had; nothing in the studio deletes it for good.
