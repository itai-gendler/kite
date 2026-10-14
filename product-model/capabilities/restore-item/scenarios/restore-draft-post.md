---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner opens the trash of posts, selects a post and chooses Restore
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: [Title, Deleted at]}
  contexts:
    studio:
      place: studio::signed-in::content-list
- text: The Product takes the post out of the trash as the draft it was
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: changes, from: In the trash, to: Draft, facts: [Deleted at]}
  contexts:
    studio:
      place: studio::signed-in::content-list
references:
- kind: code
  role: implementation
  target: internal/api/write.go#handleRestore
---

# Restore a draft post

## Trigger

The Owner deleted a draft by mistake.

## Outcome

The draft is back among the posts with everything it had.
