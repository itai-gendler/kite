---
appliesTo:
- type: capability
  id: update-app
  contexts:
  - place: studio::signed-in
  - place: cli
references:
- kind: code
  role: implementation
  target: internal/api/apps.go#handleUpdateApp
- kind: code
  role: implementation
  target: internal/cli/apps_cmd.go#agree
---

# An update waits for the owner's agreement before replacing hand edits or letting a plugin do more

An update that would replace files changed since installation, or a plugin version that loads from another site, runs another hook or injects more code than kite.lock records, is applied only once the owner agrees (ticks in the App center; --force and --yes on the command line).
