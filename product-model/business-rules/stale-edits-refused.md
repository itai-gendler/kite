---
appliesTo:
- type: capability
  id: edit-item
- type: capability
  id: change-item-status
- type: capability
  id: delete-item
- type: capability
  id: restore-item
- type: capability
  id: change-site-settings
- type: capability
  id: change-theme-settings
- type: capability
  id: rename-term
references:
- kind: code
  role: implementation
  target: internal/api/write.go#requireIfMatch
- kind: code
  role: implementation
  target: internal/api/write.go#failConflict
---

# An edit made against a version that has since changed is refused

Every change to an item, the settings or a term names the version it was made against; when what is on disk differs, nothing is overwritten and the stored version is shown.
