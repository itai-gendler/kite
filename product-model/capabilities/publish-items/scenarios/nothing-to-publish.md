---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner chooses Publish on items selected in a list
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::content-list
- text: Git sees no change in anything they name
  kind: condition
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::content-list
- text: The Product refuses, saying there is nothing to publish, and changes nothing
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::content-list
references:
- kind: code
  role: implementation
  target: internal/publish/git/preflight.go#checkPaths
---

# Publish what is already committed

## Trigger

Everything asked for is already committed.

## Outcome

No commit is made.
