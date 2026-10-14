---
appliesTo:
- type: capability
  id: install-theme
- type: capability
  id: install-plugin
references:
- kind: code
  role: implementation
  target: internal/api/themes.go#handleInstallTheme
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleInstallPlugin
---

# A theme or plugin of the same name is replaced only when the owner confirms

The installed and the uploaded versions are shown first; a plugin replaced keeps its settings.
