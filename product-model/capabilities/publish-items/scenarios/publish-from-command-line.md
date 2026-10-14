---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner runs kite publish content/posts/hello --push
  kind: actor
  actor: owner
  entities:
  - {entity: post, effect: reads, facts: []}
  contexts:
    cli:
      place: cli
- text: The Product lists the paths and the message, then commits exactly those paths
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: creates, to: Committed, facts: [Message, Paths, Branch, Hash]}
  contexts:
    cli:
      place: cli
- text: The Product pushes the commit
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
  target: internal/cli/publish_cmd.go#newPublishCmd
---

# Publish from the command line

## Trigger

The Owner publishes from a terminal.

## Outcome

The commit is on the remote.

## Decision points

### Which paths

Did the Owner name paths, or pass --all?

- Paths named → exactly those paths that git sees changed are committed.
- --all → every uncommitted path under content, static, themes, plugins, kite.yaml and kite.lock is committed.

## Edge cases

- Without --push the commit stays on the branch.
- Warnings stop the command until it is run again with --force; --no-verify commits without the hooks.
- --dry-run reports what would happen and stops.
