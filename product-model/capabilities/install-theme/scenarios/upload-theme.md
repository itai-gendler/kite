---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner drops a theme's zip archive on the Themes screen
  kind: actor
  actor: owner
  entities:
  - {entity: theme, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::themes
- text: The Product unpacks it, finds the manifest at its top or in its one folder, and checks it as a
    site loading it would
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::themes
- text: The Product puts the theme in themes/ under its own name
  kind: product
  actor: owner
  entities:
  - {entity: theme, effect: creates, facts: [Name, Version, Author, Settings it declares, Page templates,
      Menus it draws, Loads from]}
  contexts:
    studio:
      place: studio::signed-in::themes
references:
- kind: code
  role: implementation
  target: internal/api/themes.go#handleInstallTheme
---

# Upload a theme archive

## Trigger

The Owner has a theme as a zip archive.

## Outcome

The theme is listed with the others, ready to preview; the site still uses the theme it had.
