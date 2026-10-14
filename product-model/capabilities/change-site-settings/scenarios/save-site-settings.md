---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner changes the site's address and time zone and chooses Save
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::site-settings
- text: The Product checks each value and writes the changed keys to kite.yaml, against the version it
    loaded
  kind: product
  actor: owner
  entities:
  - {entity: site-settings, effect: changes, facts: [Address, Time zone]}
  contexts:
    studio:
      place: studio::signed-in::site-settings
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#handleUpdateSettings
---

# Save the site's settings

## Trigger

The Owner sets the site up for going live.

## Outcome

kite.yaml holds the new values with the rest of it untouched; the settings screen offers to publish it.
