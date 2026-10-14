---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Update on a listing with a newer version and confirms
  kind: actor
  actor: owner
  entities:
  - {entity: app, effect: reads, facts: [Installed version, Versions]}
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Product fetches and checks the new version, replaces what the theme holds and records it in
    kite.lock, keeping its settings
  kind: product
  actor: owner
  entities:
  - {entity: theme, effect: changes, facts: [Version, Installed from the index, Settings it declares,
      Page templates, Loads from]}
  contexts:
    studio:
      place: studio::signed-in::app-center
references:
- kind: code
  role: implementation
  target: internal/api/apps.go#handleUpdateApp
---

# Update a theme

## Trigger

A theme has a newer version.

## Outcome

The theme is at the new version.
