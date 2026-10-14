---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner drops a photo onto the text of a post
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product takes the GPS and place data out of the photo, leaving its pixels, orientation, camera
    and time
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product keeps the photo in the post's folder under a free name and puts it into the text where
    the cursor is
  kind: product
  actor: owner
  entities:
  - {entity: file, effect: creates, facts: [Name, Link, Size, Location removed]}
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/media.go#upload
---

# Add a photo to a post

## Trigger

The Owner illustrates a post.

## Outcome

The photo sits beside the post, linked by its name, and the editor says its location was removed; the draft saves the link with its next save.

## Edge cases

- A second file of the same name, such as two screenshot.png, gets a free name rather than replacing the first.
