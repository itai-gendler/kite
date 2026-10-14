---
kind: validation
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
- text: HEAD is not on a branch, or a merge, rebase, cherry-pick, revert or bisect is in progress
  kind: condition
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
- text: The Product refuses before committing anything and lists every reason with how to fix it
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::editor
references:
- kind: code
  role: implementation
  target: internal/publish/git/preflight.go#preflight
- kind: code
  role: implementation
  target: internal/publish/git/preflight.go#checkSizes
- kind: code
  role: implementation
  target: internal/publish/git/lock.go
---

# Publish in a repository Kite does not understand

## Trigger

The repository is in a state where a commit could rewrite someone's work.

## Outcome

Nothing is committed; the publishing panel opens on the reasons.

## Edge cases

- Also refused: git missing, a folder that is not a repository, a submodule, files git-lfs should track while it is not installed, and a file over 100 MB.
- Another publish already in progress refuses this one.
