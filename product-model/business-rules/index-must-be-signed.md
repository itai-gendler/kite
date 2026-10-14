---
appliesTo:
- type: capability
  id: browse-index
- type: capability
  id: install-theme
- type: capability
  id: install-plugin
- type: capability
  id: update-app
references:
- kind: code
  role: implementation
  target: internal/apps/sign.go
- kind: doc
  role: intent
  target: docs/reference.md
  title: Installing by name
---

# The index is used only when signed by the key Kite trusts and no older than one already used

Kite carries the public key of its own index; an index of the owner's own names its key in the settings. A stale copy cannot be passed off as current.
