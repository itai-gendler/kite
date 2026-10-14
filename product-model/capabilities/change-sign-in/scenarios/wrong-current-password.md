---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner enters a wrong current password
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::account
- text: The Product refuses the change; the attempt counts toward the limit on guesses
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::account
references:
- kind: code
  role: implementation
  target: internal/api/account.go#confirm
---

# Update with a wrong current password

## Trigger

The current password is wrong.

## Outcome

The sign-in is unchanged.
