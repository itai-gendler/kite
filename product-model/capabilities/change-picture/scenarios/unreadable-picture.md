---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner picks something that is not one of those pictures, or is too large
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::account
- text: The Product refuses it
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

# Upload something that is not a picture

## Trigger

The file cannot be read as a picture.

## Outcome

The picture is unchanged.
