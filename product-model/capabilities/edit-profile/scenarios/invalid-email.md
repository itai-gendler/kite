---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner enters something that is not an email address
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::account
- text: The Product refuses the profile
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::account
references:
- kind: code
  role: implementation
  target: internal/auth/profile.go
---

# Save an email that is not one

## Trigger

The email is malformed.

## Outcome

The profile is unchanged.
