---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Archived for declared content and saves
  kind: actor
  actor: owner
  entities:
  - {entity: declared-content, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the declared content as archived
  kind: product
  actor: owner
  entities:
  - {entity: declared-content, effect: changes, from: Published, to: Archived, facts: [Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/content/content.go#IsPublic
---

# Archive declared content

## Trigger

The Owner changes where an item of a declared kind stands.

## Outcome

The declared content is archived, with the same meaning as for a post.
