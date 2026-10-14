---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner updates one whose new version does more, without ticking
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Product refuses until the Owner agrees
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: [Agreed to do]}
  contexts:
    studio:
      place: studio::signed-in::app-center
references:
- kind: code
  role: implementation
  target: internal/api/apps.go#handleUpdateApp
---

# Update without agreeing

## Trigger

The agreement is missing.

## Outcome

The plugin stays at its version.
