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
      place: studio::signed-in::editor
- text: The remote's new commits changed paths the unpushed commit changed too
  kind: condition
  actor: owner
  entities:
  - {entity: commit, effect: reads, facts: [Paths]}
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product refuses to replay or push and shows the remote's side of those paths
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/publish/git/remote.go#remoteChange
---

# Push when the remote changed the same files

## Trigger

Both sides changed the same files.

## Outcome

The commit stays on the branch, unpushed; settling it is left to the Owner.
