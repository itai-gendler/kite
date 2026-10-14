---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner changes the accent color and a link list in the theme's settings and chooses Save
  kind: actor
  actor: owner
  entities:
  - {entity: theme, effect: reads, facts: [Settings it declares]}
  contexts:
    studio:
      place: studio::signed-in::theme-settings
- text: The Product checks each value against what the theme declares and writes the changed ones to kite.yaml,
    dropping any back at its default
  kind: product
  actor: owner
  entities:
  - {entity: site-settings, effect: changes, facts: [Theme settings]}
  - {entity: theme, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::theme-settings
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#handleUpdateSettings
---

# Save theme settings

## Trigger

The Owner adjusts how the theme looks.

## Outcome

The site is drawn with the new settings.
