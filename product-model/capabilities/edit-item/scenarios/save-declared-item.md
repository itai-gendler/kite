---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner changes the fields and weight of a published declared item and chooses Save
  kind: actor
  actor: owner
  entities:
  - {entity: declared-content, effect: reads, facts: [Fields, Weight]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product checks the fields against what the content type declares and saves
  kind: product
  actor: owner
  entities:
  - {entity: content-type, effect: reads, facts: [Fields]}
  - {entity: declared-content, effect: changes, facts: [Fields, Weight, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/write.go#handleUpdate
---

# Save declared content's fields

## Trigger

The Owner updates a project's details.

## Outcome

The declared content holds the new values.
