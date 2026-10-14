---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Update on one installed from the index
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The theme was changed by hand, so the dialog says the update replaces them and asks for a tick
  kind: condition
  actor: owner
  entities:
  - {entity: theme, effect: reads, facts: [Changed by hand]}
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Owner ticks to agree and updates
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Product replaces what the theme holds with the new version
  kind: product
  actor: owner
  entities:
  - {entity: theme, effect: changes, facts: [Version, Installed from the index, Changed by hand]}
  contexts:
    studio:
      place: studio::signed-in::app-center
references:
- kind: code
  role: implementation
  target: internal/api/apps.go#handleUpdateApp
---

# Update a theme changed by hand

## Trigger

The Owner edited an installed theme and an update comes.

## Outcome

The hand edits are replaced, as agreed.
