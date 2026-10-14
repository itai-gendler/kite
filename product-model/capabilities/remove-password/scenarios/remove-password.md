---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner enters the current password and chooses Remove password
  kind: actor
  actor: owner
  entities:
  - {entity: account, effect: reads, facts: [Comes from]}
  contexts:
    studio:
      place: studio::signed-in::account
- text: The Product deletes the account and signs this browser out of it
  kind: product
  actor: owner
  entities:
  - {entity: account, effect: removes}
  - {entity: session, effect: removes, with: account}
  contexts:
    studio:
      place: studio::signed-in::account
references:
- kind: code
  role: implementation
  target: internal/api/account.go#handleRemoveCredentials
---

# Remove the password

## Trigger

The Owner works on this computer only and wants no sign-in.

## Outcome

The studio works in local mode, without a password.
