---
availability:
- place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/ping_cmd.go#newPingCmd
- kind: code
  role: implementation
  target: internal/publish/ping/ping.go#Send
- kind: doc
  role: intent
  target: docs/reference.md
  title: Pinging after a deploy
---

# Ping update services

`kite ping`, which the deploy workflow runs once a deploy is live, tells every update service the site lists in publish.ping — Explore unless the owner said no — that the site has changed.
