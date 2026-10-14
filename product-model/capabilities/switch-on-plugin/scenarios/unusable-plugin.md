---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner tries to switch on a plugin
  kind: actor
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: [Problem]}
  contexts:
    studio:
      place: studio::signed-in::plugins
- text: The plugin does not load or fails its check
  kind: condition
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::plugins
- text: The Product refuses and says why
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::plugins
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleSwitchPlugin
---

# Switch on a plugin that cannot be used

## Trigger

The plugin is broken or does not fit this Kite.

## Outcome

The plugin stays off.
