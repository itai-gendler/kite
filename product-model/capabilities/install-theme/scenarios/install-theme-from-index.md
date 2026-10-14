---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Install on a listing in the App center
  kind: actor
  actor: owner
  entities:
  - {entity: app, effect: reads, facts: [Name, Versions, Loads from, Made by]}
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The dialog says where it goes, what it loads from, and for a community author that Kite checked
    how it loads, not what it says
  kind: condition
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Owner confirms
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Product fetches the newest version that works with this Kite, checks the archive against the
    sha256 the index gives, installs it and records it in kite.lock
  kind: product
  actor: owner
  entities:
  - {entity: theme, effect: creates, facts: [Name, Version, Author, Settings it declares, Page templates,
      Menus it draws, Loads from, Installed from the index]}
  contexts:
    studio:
      place: studio::signed-in::app-center
references:
- kind: code
  role: implementation
  target: internal/api/apps.go#handleInstallApp
- kind: code
  role: implementation
  target: internal/apps/install.go
---

# Install a theme from the index

## Trigger

The Owner found a theme in the index.

## Outcome

The theme is installed; the studio offers to preview it on the whole site before it is used.
