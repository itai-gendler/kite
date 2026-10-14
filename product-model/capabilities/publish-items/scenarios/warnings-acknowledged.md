---
kind: alternative
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
- text: The Owner has already staged changes under the post, or the remote has history the branch lacks,
    or something is over 50 MB
  kind: condition
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product does not publish yet and shows the warnings
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Owner reads them and chooses Publish anyway
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product commits what is on disk, staged parts included, and pushes
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: creates, to: Committed, facts: [Message, Paths, Branch, Hash]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The push reaches the remote
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
  target: internal/api/publish.go#handlePublish
- kind: code
  role: implementation
  target: internal/publish/git/preflight.go#checkRemote
---

# Publish despite warnings

## Trigger

Something about the repository needs reading before a commit.

## Outcome

The warnings were read and acknowledged before anything was committed.

## Edge cases

- With no remote at all, the warning says the commit will be made locally only, and the publish stops at the commit.
