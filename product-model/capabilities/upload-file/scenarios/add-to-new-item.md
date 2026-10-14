---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner drops a picture into a new item before it was ever saved
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the new post first, so it has a folder
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: creates, to: Draft, facts: [Id, Title, Slug, Text, Categories, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product keeps the picture in its new folder
  kind: product
  actor: owner
  entities:
  - {entity: file, effect: creates, facts: [Name, Link, Size, Location removed]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: web/src/components/editor/EditorPage.tsx#EditorPage
---

# Add a file to an item never saved

## Trigger

The Owner starts a post with a picture.

## Outcome

The post exists as a draft with the picture beside it.
