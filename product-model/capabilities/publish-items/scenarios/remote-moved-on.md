---
kind: edge
routes:
  studio: Studio
steps:
- text: The Owner chooses Publish in the editor
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product commits the post's folder
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: creates, to: Committed, facts: [Message, Paths, Branch, Hash]}
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: 'The remote refuses the push: it has commits the branch does not'
  kind: condition
  actor: owner
  entities:
  - {entity: commit, effect: reads, facts: [Hash]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product lists the remote's new commits and says whether the commit can go on top of them or
    which paths both changed
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/publish/git/remote.go#send
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#push
---

# Publish when the remote has moved on

## Trigger

Someone else pushed to the same branch meanwhile.

## Outcome

The commit is safe on the branch and nothing was overwritten or forced. The Owner can put it on top and push, or settle the overlap themselves.
