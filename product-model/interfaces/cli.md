---
type: cli
actors:
- owner
languages:
- en
references:
- kind: code
  role: implementation
  target: internal/cli/commands.go
- kind: code
  role: implementation
  target: cmd/kite/main.go
- kind: doc
  role: intent
  target: docs/reference.md
---

# Command line

The `kite` command, run in a site's folder: it builds, serves, publishes,
connects GitHub, installs and updates themes and plugins, pins the Kite
release, pings update services and manages the studio's account. `kitew`,
written beside a site, runs the Kite release the site pins with the same
commands. Every change it makes is to the site's files, published like any
other.
