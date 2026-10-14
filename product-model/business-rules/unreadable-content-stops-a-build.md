---
appliesTo:
- type: capability
  id: export-site
- type: capability
  id: build-site
references:
- kind: code
  role: implementation
  target: internal/serve/server.go#export
- kind: code
  role: implementation
  target: internal/site/site.go
---

# A site with content the index could not read is not exported

An export, like a deployment, refuses a site it cannot fully see and says what stopped it.
