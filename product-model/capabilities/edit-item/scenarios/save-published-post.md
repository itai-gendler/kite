---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner changes the text of a published post
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: [Text]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The post is published, so the editor says the change is kept in the browser and does not save
    it on its own
  kind: condition
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Owner chooses Save
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the change against the version the editor loaded
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: changes, facts: [Text, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: web/src/hooks/useItem.ts#autosaves
- kind: code
  role: implementation
  target: internal/api/write.go#handleUpdate
---

# Save a published post

## Trigger

The Owner corrects something in a post that is already published.

## Outcome

The change is in the post's file: a site Kite serves shows it at once, and a static site once it is published and built.
