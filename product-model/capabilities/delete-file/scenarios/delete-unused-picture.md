---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Delete on a picture in the Files list and confirms
  kind: actor
  actor: owner
  entities:
  - {entity: file, effect: reads, facts: [Name, Where it is used]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product removes the picture from the post's folder
  kind: product
  actor: owner
  entities:
  - {entity: file, effect: removes}
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/media.go#handleDeleteMedia
- kind: code
  role: implementation
  target: web/src/components/editor/Attachments.tsx
---

# Delete a picture

## Trigger

The Owner tidies a post's folder.

## Outcome

The picture is gone; anything that still used it shows nothing in its place.
