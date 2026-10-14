---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Scheduled for declared content and saves
  kind: actor
  actor: owner
  entities:
  - {entity: declared-content, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the declared content as scheduled
  kind: product
  actor: owner
  entities:
  - {entity: declared-content, effect: changes, from: Draft, to: Scheduled, facts: [Publish time, Last
        saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/content/content.go#IsPublic
---

# Schedule declared content

## Trigger

The Owner changes where an item of a declared kind stands.

## Outcome

The declared content is scheduled, with the same meaning as for a post.
