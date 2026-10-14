---
appliesTo:
- type: capability
  id: browse-site
- type: capability
  id: build-site
references:
- kind: code
  role: implementation
  target: internal/cli/serve_cmd.go#newRunCmd
- kind: code
  role: implementation
  target: internal/cli/build_cmd.go#newBuildCmd
---

# The local preview shows drafts beside public items

Drafts are drawn as they would be published, so the owner can read the whole site before publishing anything.
