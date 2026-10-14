---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner uploads a plugin already installed and chooses Replace
  kind: actor
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: [Version]}
  contexts:
    studio:
      place: studio::signed-in::plugins
- text: The Product replaces what the plugin holds and keeps its settings
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: changes, facts: [Version, Adds code to pages, Loads from, Build hooks]}
  contexts:
    studio:
      place: studio::signed-in::plugins
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleInstallPlugin
---

# Replace a plugin of the same id

## Trigger

The Owner has a newer version of a plugin.

## Outcome

The plugin is at the uploaded version with its settings as they were.
