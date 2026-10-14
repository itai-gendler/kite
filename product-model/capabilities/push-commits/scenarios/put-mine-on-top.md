---
kind: alternative
routes:
  studio: Studio
steps:
- text: The remote has commits the branch does not, and none of them changes a path the unpushed commit
    changed
  kind: condition
  actor: owner
  entities:
  - {entity: commit, effect: reads, facts: [Paths]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Owner chooses Put mine on top and push
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product replays the commit on top of the remote's commits, touching nothing else in the working
    tree
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: changes, from: Committed, to: Committed, facts: [Hash]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product pushes it and reads in what the remote brought
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: changes, from: Committed, to: Pushed, facts: [Remote]}
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/publish/git/remote.go#remoteChange
- kind: code
  role: implementation
  target: internal/publish/git/remote.go#replay
---

# Put mine on top and push

## Trigger

The remote moved on in ways that do not touch what the Owner published.

## Outcome

The commit is on the remote with a new hash, and the studio shows content the remote brought, such as another person's posts.

## Edge cases

- The replay is offered only for one unpushed commit, on a branch that shares history with the remote, with no uncommitted changes to the files the remote changed.
