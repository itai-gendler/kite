---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Publish in the bar a settings screen shows for what it changed
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::site-settings
- text: The Product commits kite.yaml, kite.lock, the changed themes and plugins and the site's uploads,
    and pushes the commit
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: creates, to: Committed, facts: [Message, Paths, Branch, Hash]}
  - {entity: theme, effect: reads, facts: []}
  - {entity: plugin, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::site-settings
- text: The push reaches the remote
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: changes, from: Committed, to: Pushed, facts: [Remote]}
  contexts:
    studio:
      place: studio::signed-in::site-settings
references:
- kind: code
  role: implementation
  target: web/src/features/settings/components/publish-bar.tsx#PublishBar
---

# Publish settings and themes

## Trigger

The Owner switched theme or changed settings, which belong to no item.

## Outcome

The site built from the repository takes the new settings and themes too.
