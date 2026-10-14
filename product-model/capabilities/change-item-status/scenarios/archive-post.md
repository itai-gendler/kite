---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Archived for a published post and saves
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the post as archived
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: changes, from: Published, to: Archived, facts: [Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/content/content.go#IsPublic
---

# Archive a post

## Trigger

The Owner wants a post kept but no longer on the site.

## Outcome

The post leaves a site Kite serves at once, and a static site at its next build.
