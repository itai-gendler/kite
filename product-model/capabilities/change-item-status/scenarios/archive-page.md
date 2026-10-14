---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Archived for a published page and saves
  kind: actor
  actor: owner
  entities:
  - {entity: page, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the page as archived
  kind: product
  actor: owner
  entities:
  - {entity: page, effect: changes, from: Published, to: Archived, facts: [Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/content/content.go#IsPublic
---

# Archive a page

## Trigger

The Owner retires a page.

## Outcome

The page is kept and is no longer on the site once built.
