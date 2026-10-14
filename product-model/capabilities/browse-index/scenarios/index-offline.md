---
kind: edge
routes:
  studio: Studio
steps:
- text: The Owner opens the App center
  kind: actor
  actor: owner
  entities:
  - {entity: app, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The index cannot be reached
  kind: condition
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Product lists the copy it kept, saying when it was fetched
  kind: product
  actor: owner
  entities:
  - {entity: app, effect: reads, facts: [Name, Versions]}
  contexts:
    studio:
      place: studio::signed-in::app-center
references:
- kind: code
  role: implementation
  target: internal/apps/client.go
---

# Browse without a network

## Trigger

The server is offline.

## Outcome

The kept copy is used and dated.
