---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Sign out under their name
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::dashboard
- text: The Product ends this browser's session
  kind: product
  actor: owner
  entities:
  - {entity: session, effect: removes}
  contexts:
    studio:
      place: studio::signed-in::dashboard
references:
- kind: code
  role: implementation
  target: internal/api/auth.go#handleLogout
---

# Sign out

## Trigger

The Owner is done.

## Outcome

The browser has to sign in again to use the studio.
