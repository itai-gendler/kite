---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner runs kite publish --push with no paths
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product pushes what is already committed
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: changes, from: Committed, to: Pushed, facts: [Remote]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/publish_cmd.go#pushCommitted
---

# Push from the command line

## Trigger

A push from a terminal failed the first time.

## Outcome

The commits are on the remote.

## Edge cases

- With --rebase, a commit the remote did not touch is put on top of the remote's commits first.
