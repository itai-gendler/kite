---
availability:
- place: studio::signed-out
- place: cli
references:
- kind: code
  role: implementation
  target: internal/api/setup.go#handleSetup
- kind: code
  role: implementation
  target: internal/api/setup.go#createSite
- kind: code
  role: implementation
  target: internal/setup/setup.go
- kind: code
  role: implementation
  target: internal/cli/init_cmd.go#newInitCmd
- kind: doc
  role: intent
  target: docs/reference.md
  title: Signing in
---

# Set up the site

Describe a new site, and on a server reachable from other machines create the one account that guards it: the setup page of a server nobody has configured, which is all such a server answers until it is finished; the Create your site page `kite run` opens in an empty folder; or `kite init` in a terminal.
