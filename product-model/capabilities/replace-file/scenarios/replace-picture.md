---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Replace on a picture in the Files list and picks a new picture of the same kind
  kind: actor
  actor: owner
  entities:
  - {entity: file, effect: reads, facts: [Name, Where it is used]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product writes the new picture under the old name, its location taken out
  kind: product
  actor: owner
  entities:
  - {entity: file, effect: changes, facts: [Size, Location removed]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/media.go#handleReplaceMedia
---

# Replace a picture

## Trigger

The Owner has a better version of a picture.

## Outcome

Every link to the picture shows the new one.
