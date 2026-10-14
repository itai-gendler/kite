---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner chooses Pin on a Kite built from source, or one whose release cannot be downloaded
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product refuses and pins nothing, as every build through kitew would fail on it
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
references:
- kind: code
  role: implementation
  target: internal/api/kite.go#handlePin
---

# Pin a release that cannot be downloaded

## Trigger

No downloadable release stands for this Kite.

## Outcome

kite.lock is unchanged.
