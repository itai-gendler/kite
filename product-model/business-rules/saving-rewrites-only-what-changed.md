---
appliesTo:
- type: capability
  id: edit-item
- type: capability
  id: change-site-settings
references:
- kind: code
  role: implementation
  target: internal/frontmatter/frontmatter.go
- kind: code
  role: implementation
  target: internal/store/file/writer.go#putSettings
- kind: doc
  role: intent
  target: docs/reference.md
  title: Design
---

# Saving rewrites only what changed

Saving an item or the settings rewrites only the keys that changed: key order, comments and flow-style lists survive, so changing a title is a one-line diff. Front matter written as TOML stays TOML.
