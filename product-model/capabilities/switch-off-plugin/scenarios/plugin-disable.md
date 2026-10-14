---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner asks the command line to switch search off
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product takes the plugin out of plugins.enabled
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: changes, from: 'On', to: 'Off', facts: []}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/plugin_cmd.go#newPluginSwitchCmd
---

# Switch a plugin off from the command line

## Trigger

The Owner runs kite plugin disable search.

## Outcome

The plugin no longer runs.
