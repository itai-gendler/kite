---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Upload picture and picks a PNG, JPEG, GIF or WebP
  kind: actor
  actor: owner
  entities:
  - {entity: account, effect: reads, facts: [Picture]}
  contexts:
    studio:
      place: studio::signed-in::account
- text: The Product keeps it on the server as a square of 256 pixels
  kind: product
  actor: owner
  entities:
  - {entity: account, effect: changes, facts: [Picture]}
  contexts:
    studio:
      place: studio::signed-in::account
references:
- kind: code
  role: implementation
  target: internal/api/account.go#handleUploadAvatar
---

# Upload a picture

## Trigger

The Owner wants a face beside their name in the studio.

## Outcome

The studio shows the picture.
