---
availability:
- place: studio::signed-in
- place: cli
domain: app-center
references:
- kind: code
  role: implementation
  target: internal/api/apps.go#handleUpdateApp
- kind: code
  role: implementation
  target: internal/cli/apps_cmd.go#newAppsUpdateCmd
---

# Update a theme or plugin

Move a theme or plugin installed from the index to a newer version (Update in the App center, or `kite apps update`). An update that would replace files changed by hand, or let a plugin do more than it was installed to do, waits until the owner agrees.
