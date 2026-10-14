---
kind: validation
routes:
  studio: Studio
steps:
- text: The Visitor submits the setup form
  kind: actor
  actor: visitor
  entities: []
  contexts:
    studio:
      place: studio::signed-out::setup
- text: The server already has an account
  kind: condition
  actor: visitor
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-out::setup
- text: The Product refuses and says to sign in instead
  kind: product
  actor: visitor
  entities: []
  contexts:
    studio:
      place: studio::signed-out::setup
references:
- kind: code
  role: implementation
  target: internal/api/setup.go#failSetup
---

# Set up a server that is already set up

## Trigger

Someone reaches the setup after it was finished.

## Outcome

Nothing changes.
