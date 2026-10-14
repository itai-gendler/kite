---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner tries to remove a plugin that is on
  kind: actor
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::plugin
- text: The Product refuses until the plugin is switched off
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::plugin
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleRemovePlugin
---

# Remove a plugin that is on

## Trigger

The plugin still runs.

## Outcome

The plugin stays.
