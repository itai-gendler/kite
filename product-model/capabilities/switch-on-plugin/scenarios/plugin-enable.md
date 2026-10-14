---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner asks the command line to switch search on
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product adds the plugin to plugins.enabled
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: changes, from: 'Off', to: 'On', facts: []}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/plugin_cmd.go#newPluginSwitchCmd
---

# Switch a plugin on from the command line

## Trigger

The Owner runs kite plugin enable search.

## Outcome

The plugin runs.
