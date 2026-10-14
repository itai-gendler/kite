---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner picks a PNG to replace a JPEG
  kind: actor
  actor: owner
  entities:
  - {entity: file, effect: reads, facts: [Name]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product refuses it, as the name and what a browser takes it for would no longer agree
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/media.go#sameKind
---

# Replace with another kind of file

## Trigger

The Owner replaces a picture with one of another kind.

## Outcome

The picture stays as it was.
