---
appliesTo:
- type: capability
  id: remove-plugin
  contexts:
  - place: studio::signed-in
  - place: cli
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleRemovePlugin
---

# A plugin that is on is never removed

It is switched off first, which makes removing it a decision about a plugin the site already does without.
