---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner chooses Push again
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::dashboard
- text: Everything committed on the branch is already on the remote
  kind: condition
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::dashboard
- text: The Product says there is nothing to push
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::dashboard
references:
- kind: code
  role: implementation
  target: internal/publish/git/remote.go#Push
---

# Push with nothing to push

## Trigger

The branch is level with its remote.

## Outcome

Nothing changes.
