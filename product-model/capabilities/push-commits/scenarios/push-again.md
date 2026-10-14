---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Push N commits on the dashboard
  kind: actor
  actor: owner
  entities:
  - {entity: commit, effect: reads, facts: [Paths]}
  contexts:
    studio:
      place: studio::signed-in::dashboard
- text: The Product pushes the branch to its remote, never forcing it
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: changes, from: Committed, to: Pushed, facts: [Remote]}
  contexts:
    studio:
      place: studio::signed-in::dashboard
references:
- kind: code
  role: implementation
  target: internal/publish/git/remote.go#Push
---

# Push again

## Trigger

A publish committed but its push did not go through.

## Outcome

The commits are on the remote.
