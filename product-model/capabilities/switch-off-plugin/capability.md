---
availability:
- place: studio::signed-in
- place: cli
domain: plugins
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleSwitchPlugin
- kind: code
  role: implementation
  target: internal/cli/plugin_cmd.go#newPluginSwitchCmd
---

# Switch a plugin off

Stop a plugin running (Switch off, or `kite plugin disable`); its settings stay in kite.yaml for when it comes back.
