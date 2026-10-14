---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Publish N changes on the dashboard
  kind: actor
  actor: owner
  entities:
  - {entity: commit, effect: reads, facts: [Paths]}
  contexts:
    studio:
      place: studio::signed-in::dashboard
- text: The dialog lists every uncommitted path under content, static, themes, plugins, kite.yaml and
    kite.lock
  kind: condition
  actor: owner
  entities:
  - {entity: theme, effect: reads, facts: []}
  - {entity: plugin, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::dashboard
- text: The Owner confirms
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::dashboard
- text: The Product commits exactly those paths and pushes the commit
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: creates, to: Committed, facts: [Message, Paths, Branch, Hash]}
  contexts:
    studio:
      place: studio::signed-in::dashboard
- text: The push reaches the remote
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: changes, from: Committed, to: Pushed, facts: [Remote]}
  contexts:
    studio:
      place: studio::signed-in::dashboard
references:
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#watched
- kind: code
  role: implementation
  target: web/src/features/dashboard/components/cards.tsx#DeliveryOverview
---

# Publish every change

## Trigger

The Owner has saved several things and wants all of them on the site.

## Outcome

Every change Kite manages is committed and pushed. Changes elsewhere in the project — templates and language packs of the site's own in layouts/ and i18n/, kitew, workflows — are not carried.
