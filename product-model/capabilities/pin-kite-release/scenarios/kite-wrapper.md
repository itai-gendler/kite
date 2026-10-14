---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner runs kite wrapper
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product pins the running release in kite.lock and writes kitew and kitew.ps1 beside it
  kind: product
  actor: owner
  entities:
  - {entity: site-settings, effect: changes, facts: [Pinned Kite release, Pinned release checksums]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/wrapper_cmd.go#newWrapperCmd
---

# Pin with kite wrapper

## Trigger

The Owner moves the pin from a terminal.

## Outcome

kite.lock, kitew and kitew.ps1 are ready to commit.

## Edge cases

- A deploy workflow that installs Kite itself is pointed out, with the build step to change to sh ./kitew build.
