---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner runs kite auth set-password in a site that has an account
  kind: actor
  actor: owner
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    cli:
      place: cli
- text: The Product stores the new password
  kind: product
  actor: owner
  entities:
  - {entity: account, effect: changes, facts: [User name, Password]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/auth_cmd.go#newAuthSetPasswordCmd
---

# Change the password from the command line

## Trigger

The Owner forgot the password.

## Outcome

The new password takes effect at the server's next start.
