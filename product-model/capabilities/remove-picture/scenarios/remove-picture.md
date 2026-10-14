---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Remove under the picture
  kind: actor
  actor: owner
  entities:
  - {entity: account, effect: reads, facts: [Picture]}
  contexts:
    studio:
      place: studio::signed-in::account
- text: The Product deletes the kept picture
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
  target: internal/api/account.go#handleRemoveAvatar
---

# Remove the picture

## Trigger

The Owner no longer wants a picture.

## Outcome

The studio shows the Owner's initials.
