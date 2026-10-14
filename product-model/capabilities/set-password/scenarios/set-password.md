---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner gives a user name and a password of at least 8 characters in the account settings and
    chooses Set password
  kind: actor
  actor: owner
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::account
- text: The Product stores the account and signs this browser in with it
  kind: product
  actor: owner
  entities:
  - {entity: account, effect: creates, facts: [User name, Password, Comes from]}
  - {entity: session, effect: creates, facts: [Expires, Remembered], with: account}
  contexts:
    studio:
      place: studio::signed-in::account
references:
- kind: code
  role: implementation
  target: internal/api/account.go#handleSetCredentials
---

# Set a password

## Trigger

The Owner is about to serve the studio somewhere other machines can reach.

## Outcome

The studio asks for the password from now on.

## Edge cases

- A user name left empty is admin.
