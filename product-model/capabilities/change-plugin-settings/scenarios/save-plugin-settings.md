---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner changes a plugin's settings and saves
  kind: actor
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: [Settings]}
  contexts:
    studio:
      place: studio::signed-in::plugin
- text: The Product checks the values against what the plugin declares and writes them to kite.yaml
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: changes, facts: [Settings]}
  contexts:
    studio:
      place: studio::signed-in::plugin
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go
---

# Save plugin settings

## Trigger

The Owner configures a plugin, such as the comments service it uses.

## Outcome

The plugin works with the new settings.
