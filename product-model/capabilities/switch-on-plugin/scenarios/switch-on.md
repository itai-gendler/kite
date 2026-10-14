---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner switches a plugin on
  kind: actor
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: [Name, Adds code to pages, Loads from]}
  contexts:
    studio:
      place: studio::signed-in::plugins
- text: The Product checks the plugin and adds it to plugins.enabled, after the ones already on
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: changes, from: 'Off', to: 'On', facts: []}
  contexts:
    studio:
      place: studio::signed-in::plugins
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleSwitchPlugin
---

# Switch a plugin on

## Trigger

The Owner wants what a plugin adds.

## Outcome

The plugin runs on the site.
