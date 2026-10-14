---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner chooses a password of fewer than 8 characters
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::account
- text: The Product refuses it; length is all that is asked for
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::account
references:
- kind: code
  role: implementation
  target: internal/auth/account.go
---

# Set a password that is too short

## Trigger

The password is too short.

## Outcome

The studio stays in local mode.
