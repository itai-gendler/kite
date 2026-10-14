---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Scheduled and a publish time for a draft page, and saves
  kind: actor
  actor: owner
  entities:
  - {entity: page, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the page as scheduled
  kind: product
  actor: owner
  entities:
  - {entity: page, effect: changes, from: Draft, to: Scheduled, facts: [Publish time, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/content/content.go#IsPublic
---

# Schedule a page

## Trigger

The Owner wants a page to appear later.

## Outcome

The page appears once its time has passed and the site is built or served after it.
