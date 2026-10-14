---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner uploads an archive of a theme already installed
  kind: actor
  actor: owner
  entities:
  - {entity: theme, effect: reads, facts: [Name, Version]}
  contexts:
    studio:
      place: studio::signed-in::themes
- text: The Product does not install yet and shows the installed and uploaded versions
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::themes
- text: The Owner chooses Replace
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::themes
- text: The Product replaces what the theme holds with the archive's contents
  kind: product
  actor: owner
  entities:
  - {entity: theme, effect: changes, facts: [Version, Settings it declares, Page templates, Menus it draws,
      Loads from]}
  contexts:
    studio:
      place: studio::signed-in::themes
references:
- kind: code
  role: implementation
  target: internal/api/themes.go#handleInstallTheme
---

# Replace a theme of the same name

## Trigger

The Owner has a newer version of an installed theme.

## Outcome

The theme is at the uploaded version.
