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

# Switch a plugin on

Make a plugin run, after those already on (Switch on, or `kite plugin enable`). It is checked first; its code goes on pages and its hooks run from the next build or page served.
