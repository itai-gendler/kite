---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner runs kite auth remove
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product deletes the stored account
  kind: product
  actor: owner
  entities:
  - {entity: account, effect: removes}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/auth_cmd.go#newAuthRemoveCmd
---

# Remove the password from the command line

## Trigger

The Owner takes the account away from a terminal.

## Outcome

No account is stored: a server started on this computer works in local mode, and one reachable from other machines waits for setup.
