---
availability:
- place: studio::signed-in
- place: cli
domain: app-center
references:
- kind: code
  role: implementation
  target: internal/api/apps.go#handleApps
- kind: code
  role: implementation
  target: internal/apps/client.go
- kind: code
  role: implementation
  target: internal/cli/apps_cmd.go#newAppsSearchCmd
---

# Browse the index

Look through the themes and plugins the index lists — by word and by who makes them — with what each loads, injects and runs, and which installed ones have a newer version, were yanked or were taken off (the App center, `kite apps search`, `kite apps outdated`). The server fetches the signed index at most once an hour, or at once with Check again, so the browser never reaches the index's addresses.
