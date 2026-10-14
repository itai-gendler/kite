---
kind: edge
routes:
  studio: Studio
steps:
- text: The Owner chooses Save
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::theme-settings
- text: kite.yaml changed since the settings were loaded
  kind: condition
  actor: owner
  entities:
  - {entity: site-settings, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::theme-settings
- text: The Product refuses and asks the Owner to reload before editing again
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::theme-settings
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#handleUpdateSettings
---

# Save settings that changed elsewhere

## Trigger

Someone changed kite.yaml meanwhile.

## Outcome

Nothing is overwritten.
