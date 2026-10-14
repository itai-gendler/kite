---
kind: primary
result: achieved
routes:
  studio: Studio
steps:
- text: The Owner chooses Write a post on the dashboard
  kind: actor
  actor: owner
  capability: create-item
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::dashboard
- text: The Owner types a title and the opening of the text
  kind: actor
  actor: owner
  capability: create-item
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the new post as a draft and moves the editor to its own address
  kind: product
  actor: owner
  capability: create-item
  entities:
  - {entity: post, effect: creates, to: Draft, facts: [Id, Title, Slug, Text, Categories, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Owner goes on writing
  kind: actor
  actor: owner
  capability: edit-item
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the draft again shortly after typing stops
  kind: product
  actor: owner
  capability: edit-item
  entities:
  - {entity: post, effect: changes, facts: [Text, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
---

# Start a post and keep writing

## Trigger

The Owner starts writing from the dashboard.

## Outcome

The post is a saved draft and the Owner is writing it in its own editor.
