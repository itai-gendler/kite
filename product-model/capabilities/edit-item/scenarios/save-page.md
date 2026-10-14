---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner changes a page's text and chooses Save
  kind: actor
  actor: owner
  entities:
  - {entity: page, effect: reads, facts: [Text]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the change against the version the editor loaded
  kind: product
  actor: owner
  entities:
  - {entity: page, effect: changes, facts: [Text, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/write.go#handleUpdate
---

# Save a page

## Trigger

The Owner changes a page.

## Outcome

The page's file holds the change.
