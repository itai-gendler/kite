---
appliesTo:
- type: entity
  id: post
  effect: creates
  contexts:
  - place: cli
- type: entity
  id: post
  effect: changes
  contexts:
  - place: cli
- type: entity
  id: page
  effect: creates
  contexts:
  - place: cli
- type: entity
  id: page
  effect: changes
  contexts:
  - place: cli
- type: entity
  id: file
  effect: creates
  contexts:
  - place: cli
- type: entity
  id: commit
  effect: creates
  contexts:
  - place: cli
- type: entity
  id: commit
  effect: changes
  contexts:
  - place: cli
- type: entity
  id: github-connection
  effect: creates
  contexts:
  - place: cli
- type: entity
  id: github-connection
  effect: removes
  contexts:
  - place: cli
- type: entity
  id: site-settings
  effect: changes
  contexts:
  - place: cli
- type: entity
  id: theme
  effect: creates
  contexts:
  - place: cli
- type: entity
  id: theme
  effect: changes
  contexts:
  - place: cli
- type: entity
  id: theme
  effect: removes
  contexts:
  - place: cli
- type: entity
  id: plugin
  effect: creates
  contexts:
  - place: cli
- type: entity
  id: plugin
  effect: changes
  contexts:
  - place: cli
- type: entity
  id: plugin
  effect: removes
  contexts:
  - place: cli
- type: entity
  id: account
  effect: creates
  contexts:
  - place: cli
- type: entity
  id: account
  effect: changes
  contexts:
  - place: cli
- type: entity
  id: account
  effect: removes
  contexts:
  - place: cli
permits:
- actors: [owner]
references:
- kind: code
  role: implementation
  target: internal/cli/commands.go
- kind: code
  role: implementation
  target: internal/project/project.go
---

# On the command line the owner changes the site directly

The commands work on the site's files directly: they change content and settings, commit and push, connect GitHub and manage the account without a studio session or a server.
