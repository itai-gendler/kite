---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Use on a theme and confirms
  kind: actor
  actor: owner
  entities:
  - {entity: theme, effect: reads, facts: [Name, Problem]}
  contexts:
    studio:
      place: studio::signed-in::themes
- text: The Product sets the site's theme in kite.yaml
  kind: product
  actor: owner
  entities:
  - {entity: site-settings, effect: changes, facts: [Theme in use]}
  - {entity: theme, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::themes
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#handleUpdateSettings
---

# Switch the site to a theme

## Trigger

The Owner has chosen how the site should look.

## Outcome

The site is drawn with the theme at once where Kite serves it; the settings screens offer to publish kite.yaml and the theme's folder.
