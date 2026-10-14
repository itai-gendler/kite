---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Overwrite with mine on a post that changed elsewhere
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the Owner's version against the stored version it was shown
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: changes, facts: [Title, Text, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: web/src/hooks/useItem.ts#useItem
---

# Overwrite with mine after a conflict

## Trigger

The Owner has read both versions and keeps their own.

## Outcome

The Owner's version is saved over the one they were shown; a change made after that would be refused again.
