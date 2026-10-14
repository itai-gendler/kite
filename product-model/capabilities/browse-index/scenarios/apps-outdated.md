---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner asks the command line what is outdated
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product lists what is installed from the index and has a newer version, or was yanked or taken
    off
  kind: product
  actor: owner
  entities:
  - {entity: app, effect: reads, facts: [Name, Versions, Yanked, No longer listed, Installed version]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/apps_cmd.go#newAppsOutdatedCmd
---

# List what is outdated from the command line

## Trigger

The Owner runs kite apps outdated.

## Outcome

The Owner knows what can be updated.

## Edge cases

- kite apps search lists what the index offers; every word given has to match.
