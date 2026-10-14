---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Preview on a theme the site does not use
  kind: actor
  actor: owner
  entities:
  - {entity: theme, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::themes
- text: The Product draws the site with that theme and the settings as edited, throughout
  kind: product
  actor: owner
  entities:
  - {entity: theme, effect: reads, facts: [Name, Settings it declares]}
  - {entity: site-settings, effect: reads, facts: [Theme settings]}
  contexts:
    studio:
      place: studio::signed-in::theme-settings
references:
- kind: code
  role: implementation
  target: internal/api/previews.go#handleOpenPreview
---

# Try a theme on the whole site

## Trigger

The Owner wants to see a theme on their own content.

## Outcome

The Owner sees the site in the theme; the site itself has not changed.
