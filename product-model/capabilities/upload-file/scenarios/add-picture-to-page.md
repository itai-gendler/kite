---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner drops a picture onto the text of a page
  kind: actor
  actor: owner
  entities:
  - {entity: page, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product keeps the picture among the site's own uploads in static/uploads/ and links it from
    the site's root
  kind: product
  actor: owner
  entities:
  - {entity: file, effect: creates, facts: [Name, Link, Size, Location removed]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/store/file/writer.go#putMedia
---

# Add a picture to a page

## Trigger

The Owner adds a picture to a page, which has no folder of its own.

## Outcome

The picture is among the site's uploads, linked from the site's root.
