---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner enters a new password and the current one and chooses Update sign-in
  kind: actor
  actor: owner
  entities:
  - {entity: account, effect: reads, facts: [User name, Comes from]}
  contexts:
    studio:
      place: studio::signed-in::account
- text: The Product checks the current password and stores the new one
  kind: product
  actor: owner
  entities:
  - {entity: account, effect: changes, facts: [User name, Password]}
  contexts:
    studio:
      place: studio::signed-in::account
- text: Every session ends but this browser's, which is renewed
  kind: product
  actor: owner
  entities:
  - {entity: session, as: others, effect: removes}
  - {entity: session, as: this, effect: changes, facts: [Expires]}
  contexts:
    studio:
      place: studio::signed-in::account
references:
- kind: code
  role: implementation
  target: internal/api/account.go#handleSetCredentials
---

# Update the sign-in

## Trigger

The Owner changes the password.

## Outcome

The new password signs in; other browsers have to sign in again.
