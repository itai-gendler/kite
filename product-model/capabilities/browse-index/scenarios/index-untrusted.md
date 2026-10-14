---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner chooses Check again
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The index is not signed by the key Kite trusts for it, or is older than one already used
  kind: condition
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::app-center
- text: The Product does not use it and says the signature check failed
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::app-center
references:
- kind: code
  role: implementation
  target: internal/apps/sign.go
---

# Browse an index that fails its signature

## Trigger

A stale or tampered copy of the index is served.

## Outcome

Nothing from that index is listed or installed.
