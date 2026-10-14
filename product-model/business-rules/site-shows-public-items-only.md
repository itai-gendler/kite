---
appliesTo:
- type: capability
  id: browse-site
- type: capability
  id: build-site
references:
- kind: code
  role: implementation
  target: internal/content/content.go#IsPublic
- kind: code
  role: implementation
  target: internal/cli/serve_cmd.go#newServeCmd
---

# The site shows only public items

Drafts, archived and trashed items and items whose time has not come are left out of what is served and built.
