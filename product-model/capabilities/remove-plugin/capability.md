---
availability:
- place: studio::signed-in
- place: cli
domain: plugins
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleRemovePlugin
- kind: code
  role: implementation
  target: internal/cli/plugin_cmd.go#newPluginRemoveCmd
---

# Remove a plugin

Delete an installed plugin's folder (Remove, or `kite plugin remove`) once it is switched off. Its settings stay in kite.yaml.
