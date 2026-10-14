---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner runs kite auth set-password and types the password twice
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product stores the account
  kind: product
  actor: owner
  entities:
  - {entity: account, effect: creates, facts: [User name, Password, Comes from]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/auth_cmd.go#newAuthSetPasswordCmd
---

# Set a password from the command line

## Trigger

The Owner gives a server its account before it is reachable.

## Outcome

The next start of the server asks for a sign-in instead of waiting for setup.
