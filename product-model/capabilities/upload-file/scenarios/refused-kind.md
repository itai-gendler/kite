---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner drops an archive or a script, or anything over 32 MB, onto a post
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product refuses it and keeps nothing
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/media.go#allowedMedia
---

# Add a file of a kind the site does not host

## Trigger

The Owner tries to attach something the site does not host.

## Outcome

Nothing is stored; the editor says why. Pictures, audio, video, PDFs, text, CSV, JSON and fonts are taken.
