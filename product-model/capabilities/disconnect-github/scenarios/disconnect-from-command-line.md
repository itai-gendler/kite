---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner runs kite github disconnect
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product forgets the kept token
  kind: product
  actor: owner
  entities:
  - {entity: github-connection, effect: removes}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/github_cmd.go#newGitHubDisconnectCmd
---

# Disconnect from the command line

## Trigger

The Owner disconnects from a terminal.

## Outcome

The token is forgotten.
