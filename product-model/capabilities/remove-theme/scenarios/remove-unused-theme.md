---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Remove on a theme the site does not use and confirms
  kind: actor
  actor: owner
  entities:
  - {entity: theme, effect: reads, facts: [Name, In use, Built in]}
  contexts:
    studio:
      place: studio::signed-in::themes
- text: The Product deletes the theme's folder
  kind: product
  actor: owner
  entities:
  - {entity: theme, effect: removes}
  contexts:
    studio:
      place: studio::signed-in::themes
references:
- kind: code
  role: implementation
  target: internal/api/themes.go#handleRemoveTheme
---

# Remove a theme

## Trigger

The Owner no longer wants a theme.

## Outcome

The theme is gone from themes/.
