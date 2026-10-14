---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner asks the command line to update everything from the index
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product updates every theme installed from the index that has a newer version, leaving alone
    any changed by hand
  kind: product
  actor: owner
  entities:
  - {entity: theme, effect: changes, facts: [Version, Installed from the index]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/apps_cmd.go#newAppsUpdateCmd
---

# Update from the command line

## Trigger

The Owner runs kite apps update.

## Outcome

Everything that could be updated is.

## Edge cases

- --force updates a package changed by hand; --yes agrees to a plugin doing more.
- A package installed from an archive or a folder is offered updates only when its homepage is the repository the index names.
