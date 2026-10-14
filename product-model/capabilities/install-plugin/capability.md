---
availability:
- place: studio::signed-in
- place: cli
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleInstallPlugin
- kind: code
  role: implementation
  target: internal/api/apps.go#handleInstallApp
- kind: code
  role: implementation
  target: internal/cli/plugin_cmd.go#newPluginAddCmd
---

# Install a plugin

Add a plugin to plugins/, switched off: upload its zip archive on the Plugins page, Install in the App center, or `kite plugin add <name[@version]|archive|folder>`. Before it is installed the owner is shown what it adds to pages and which other sites its code loads from; a plugin from the index is recorded in kite.lock with what it was installed to do.
