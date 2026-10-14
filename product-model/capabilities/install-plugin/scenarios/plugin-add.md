---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner asks the command line to add search by name
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product installs it from the index, switched off, and records it in kite.lock
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: creates, to: 'Off', facts: [Id, Name, Version, Adds code to pages, Loads
        from, Build hooks, Installed from the index, Agreed to do]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/plugin_cmd.go#newPluginAddCmd
---

# Install a plugin from the command line

## Trigger

The Owner runs kite plugin add search.

## Outcome

The plugin is in plugins/, off.
