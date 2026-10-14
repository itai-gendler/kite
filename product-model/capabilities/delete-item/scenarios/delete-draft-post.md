---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Delete in the status menu of a draft post and confirms
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product moves the post to the trash, noting when, against the version the editor loaded
  kind: product
  actor: owner
  entities:
  - {entity: post, effect: changes, from: Draft, to: In the trash, facts: [Deleted at]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/api/write.go#handleDelete
---

# Delete a draft post

## Trigger

The Owner no longer wants a draft.

## Outcome

The post is in the trash with its folder intact, and the Owner is back at the list.

## Edge cases

- A post that changed on disk since it was loaded is refused rather than deleted.
