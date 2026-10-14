---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner switches a plugin off
  kind: actor
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::plugins
- text: The Product takes the plugin out of plugins.enabled
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: changes, from: 'On', to: 'Off', facts: []}
  contexts:
    studio:
      place: studio::signed-in::plugins
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleSwitchPlugin
---

# Switch a plugin off

## Trigger

The Owner no longer wants what a plugin adds.

## Outcome

The plugin no longer runs; its settings are kept.
