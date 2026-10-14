---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Preview while writing a post
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product draws the post as written so far, with the site's theme, template and plugin hooks
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: [Title, Text, Cover, Template]}
  - {entity: theme, effect: reads, facts: []}
  - {entity: plugin, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/preview.go#handlePreview
---

# Preview a draft

## Trigger

The Owner wants to see how a post will look.

## Outcome

The preview shows the post as a build would, and follows the text as it scrolls.
