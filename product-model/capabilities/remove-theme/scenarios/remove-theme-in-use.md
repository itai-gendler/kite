---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner tries to remove the theme the site uses
  kind: actor
  actor: owner
  entities:
  - {entity: theme, effect: reads, facts: [In use]}
  contexts:
    studio:
      place: studio::signed-in::themes
- text: The Product refuses until the site switches away from it
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::themes
references:
- kind: code
  role: implementation
  target: internal/api/themes.go#handleRemoveTheme
---

# Remove the theme in use

## Trigger

The theme is in use.

## Outcome

The theme stays.
