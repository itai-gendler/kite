---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner deletes a published declared item from its list and confirms
  kind: actor
  actor: owner
  entities:
  - {entity: declared-content, effect: reads, facts: [Title]}
  contexts:
    studio:
      place: studio::signed-in::content-list
- text: The Product moves it to the trash
  kind: product
  actor: owner
  entities:
  - {entity: declared-content, effect: changes, from: Published, to: In the trash, facts: [Deleted at]}
  contexts:
    studio:
      place: studio::signed-in::content-list
references:
- kind: code
  role: implementation
  target: internal/api/write.go#handleDelete
---

# Delete declared content

## Trigger

The Owner drops a project.

## Outcome

The declared content is in the trash and leaves the site once built.
