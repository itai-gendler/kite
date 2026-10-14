---
kind: validation
routes:
  studio: Studio
steps:
- text: The Visitor chooses a password of fewer than 8 characters and chooses Finish
  kind: actor
  actor: visitor
  entities: []
  contexts:
    studio:
      place: studio::signed-out::setup
- text: The Product refuses before rewriting anything
  kind: product
  actor: visitor
  entities: []
  contexts:
    studio:
      place: studio::signed-out::setup
references:
- kind: code
  role: implementation
  target: internal/api/setup.go#handleSetup
---

# Set up with a password that is too short

## Trigger

The password is too short.

## Outcome

The site's settings and the account are as they were; the setup is still open.
