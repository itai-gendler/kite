---
kind: edge
routes:
  studio: Studio
steps:
- text: The Owner writes a shortcode that nothing defines
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product says which shortcode is missing and on which line, instead of drawing the post
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: [Text]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/render/shortcode.go
---

# Preview text calling an unknown shortcode

## Trigger

The text calls a shortcode nobody defines.

## Outcome

The preview names the shortcode and its line; a build would stop on it the same way.
