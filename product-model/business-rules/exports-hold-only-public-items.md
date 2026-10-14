---
appliesTo:
- type: capability
  id: export-site
  contexts:
  - place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/serve/server.go#export
---

# An export holds only public items, whatever the server shows

A studio that serves drafts for a preview still exports without them.
