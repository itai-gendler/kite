---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Published for a draft page and saves
  kind: actor
  actor: owner
  entities:
  - {entity: page, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the page as published, its publish time taken as now
  kind: product
  actor: owner
  entities:
  - {entity: page, effect: changes, from: Draft, to: Published, facts: [Publish time, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: web/src/components/editor/PublishMenu.tsx#PublishMenu
---

# Mark a page published

## Trigger

The Owner decides a page is ready.

## Outcome

The page is published.
