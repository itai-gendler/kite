---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner saves a value that does not fit its field
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::plugin
- text: The Product refuses the save and names the setting
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::plugin
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#handleUpdateSettings
---

# Save a value the plugin does not accept

## Trigger

A value does not fit.

## Outcome

Nothing is written.
