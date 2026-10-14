---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner opens the account settings of a server whose account comes from its environment
  kind: actor
  actor: owner
  entities:
  - {entity: account, effect: reads, facts: [Comes from]}
  contexts:
    studio:
      place: studio::signed-in::account
- text: The Product offers no change and says to change KITE_ADMIN_USER and KITE_ADMIN_PASSWORD where
    they are set and restart
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::account
references:
- kind: code
  role: implementation
  target: internal/api/account.go#failAccount
---

# Change an account from the environment

## Trigger

The account is given by the server's environment.

## Outcome

The account can only be changed where it is set.
