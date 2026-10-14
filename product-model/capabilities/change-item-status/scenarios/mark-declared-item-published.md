---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Published for declared content and saves
  kind: actor
  actor: owner
  entities:
  - {entity: declared-content, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the declared content as published
  kind: product
  actor: owner
  entities:
  - {entity: declared-content, effect: changes, from: Draft, to: Published, facts: [Publish time, Last
        saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/content/content.go#IsPublic
---

# Mark declared content published

## Trigger

The Owner changes where an item of a declared kind stands.

## Outcome

The declared content is published, with the same meaning as for a post.
