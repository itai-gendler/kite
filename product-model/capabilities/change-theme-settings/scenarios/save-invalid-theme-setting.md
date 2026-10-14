---
kind: validation
routes:
  studio: Studio
steps:
- text: 'The Owner writes a color as something other than #rrggbb and chooses Save'
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::theme-settings
- text: The Product refuses the save and names the setting
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::theme-settings
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#checkThemeSetting
---

# Save a value the theme does not accept

## Trigger

A value does not fit its field.

## Outcome

Nothing is written.
