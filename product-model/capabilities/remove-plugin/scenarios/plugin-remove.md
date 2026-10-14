---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner asks the command line to remove search
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product deletes the plugin's folder
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: removes, from: 'Off'}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/plugin_cmd.go#newPluginRemoveCmd
---

# Remove a plugin from the command line

## Trigger

The Owner runs kite plugin remove search.

## Outcome

The plugin is gone.

## Edge cases

- A plugin that is on is refused until kite plugin disable has switched it off.
