---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Remove on a plugin that is off and confirms
  kind: actor
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::plugin
- text: The Product deletes the plugin's folder
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: removes, from: 'Off'}
  contexts:
    studio:
      place: studio::signed-in::plugin
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleRemovePlugin
---

# Remove a plugin

## Trigger

The Owner no longer wants a plugin.

## Outcome

The plugin is gone from plugins/; its settings remain in kite.yaml.
