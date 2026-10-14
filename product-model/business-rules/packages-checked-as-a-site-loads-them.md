---
appliesTo:
- type: capability
  id: install-theme
- type: capability
  id: install-plugin
- type: capability
  id: update-app
references:
- kind: code
  role: implementation
  target: internal/archive/archive.go
- kind: code
  role: implementation
  target: internal/apps/install.go
---

# A theme or plugin is checked the way a site loads it before it is installed

An archive is unpacked and loaded before anything is written; one from the index is first checked against the sha256 the index names, whatever address served it.
