---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner opens the App center and searches for docs
  kind: actor
  actor: owner
  entities:
  - {entity: app, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Product lists what the index offers that matches, with what each does to the site and which
    installed ones can be updated
  kind: product
  actor: owner
  entities:
  - {entity: app, effect: reads, facts: [Kind, Name, Description, Made by, Versions, Needs Kite, Loads
        from, Code on pages, Build hooks, Installed version]}
  contexts:
    studio:
      place: studio::signed-in::app-center
references:
- kind: code
  role: implementation
  target: internal/api/apps.go#handleApps
---

# Browse the App center

## Trigger

The Owner looks for a theme or a plugin.

## Outcome

The Owner sees what the index offers and what it would do to the site.
