---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner opens the status menu of a draft post and chooses Published
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: [Publish time]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product takes the publish time as now, as the post has none yet
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Owner chooses Save
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product saves the post as published
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: changes, from: Draft, to: Published, facts: [Publish time, Last saved]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: web/src/components/editor/PublishMenu.tsx#PublishMenu
- kind: code
  role: implementation
  target: internal/content/content.go#IsPublic
---

# Mark a post published

## Trigger

The Owner decides a draft is ready for readers.

## Outcome

The post is published: a site Kite serves shows it at once; a static site shows it once it is committed, pushed and built.

## Edge cases

- A post already carrying a publish time keeps it.
- A published post whose publish time is in the future waits for it, as in Hugo and Jekyll, and the menu says from when it will be on the site.
