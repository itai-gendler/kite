---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner restores declared content from the trash
  kind: actor
  actor: owner
  entities:
  - {entity: declared-content, effect: reads, facts: [Title, Deleted at]}
  contexts:
    studio:
      place: studio::signed-in::content-list
- text: The Product takes it out of the trash, published as it was
  kind: product
  actor: owner
  entities:
  - {entity: declared-content, effect: changes, from: In the trash, to: Published, facts: [Deleted at]}
  contexts:
    studio:
      place: studio::signed-in::content-list
references:
- kind: code
  role: implementation
  target: internal/api/write.go#handleRestore
---

# Restore declared content

## Trigger

The Owner wants a project back.

## Outcome

The declared content is published again.
