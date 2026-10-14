---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner tries to use a theme listed as unusable
  kind: actor
  actor: owner
  entities:
  - {entity: theme, effect: reads, facts: [Problem]}
  contexts:
    studio:
      place: studio::signed-in::themes
- text: The Product refuses and says why it cannot be used
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::themes
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#usableTheme
---

# Use a theme that cannot be used

## Trigger

The theme failed its checks.

## Outcome

The site keeps its theme.
