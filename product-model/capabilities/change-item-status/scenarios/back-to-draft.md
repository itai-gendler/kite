---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Draft for a published post and saves
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the post as a draft
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: changes, from: Published, to: Draft, facts: [Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: web/src/hooks/useItem.ts#autosaves
---

# Take a post back to draft

## Trigger

The Owner withdraws a post to rework it.

## Outcome

The post is no longer on the site once built, and from now on its changes save themselves again.
