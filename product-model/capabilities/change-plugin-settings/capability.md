---
availability:
- place: studio::signed-in
domain: plugins
references:
- kind: code
  role: implementation
  target: web/src/features/plugins/plugin.tsx
- kind: code
  role: implementation
  target: internal/api/settings.go#handleUpdateSettings
---

# Change plugin settings

Edit the settings a plugin declares on its own page and save them; they are stored under plugins.settings.<id> in kite.yaml.
