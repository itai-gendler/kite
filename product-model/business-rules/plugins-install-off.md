---
appliesTo:
- type: capability
  id: install-plugin
  contexts:
  - place: studio::signed-in
  - place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/plugin_cmd.go#newPluginAddCmd
---

# A plugin is installed switched off

It does nothing until the owner switches it on.
