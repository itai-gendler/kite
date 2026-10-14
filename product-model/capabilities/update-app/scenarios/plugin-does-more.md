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
- text: The new version loads from another site, runs another hook or injects more code than the plugin
    was agreed to do
  kind: condition
  actor: owner
  entities:
  - {entity: plugin, effect: reads, facts: [Agreed to do]}
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Owner ticks to agree to each and updates
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Product installs the new version and records what it now does
  kind: product
  actor: owner
  entities:
  - {entity: plugin, effect: changes, facts: [Version, Installed from the index, Agreed to do, Adds code
        to pages, Loads from, Build hooks]}
  contexts:
    studio:
      place: studio::signed-in::app-center
references:
- kind: code
  role: implementation
  target: internal/api/apps.go#plan
---

# Update a plugin that does more

## Trigger

A plugin's new version asks for more.

## Outcome

The plugin is updated with the Owner's agreement recorded.
