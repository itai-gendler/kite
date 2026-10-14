---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Build with the running release on the Deploy screen
  kind: actor
  actor: owner
  entities:
  - {entity: site-settings, effect: reads, facts: [Pinned Kite release]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product fetches the release's checksums and pins it in kite.lock
  kind: product
  actor: owner
  entities:
  - {entity: site-settings, effect: changes, facts: [Pinned Kite release, Pinned release checksums]}
  contexts:
    studio:
      place: studio::signed-in::deploy
references:
- kind: code
  role: implementation
  target: internal/api/kite.go#handlePin
---

# Build with the running release

## Trigger

kite.lock pins another release than the one the Owner runs, or none.

## Outcome

kite.lock pins the running release; once it is published, the deploy builds with it.

## Edge cases

- When the checksums cannot be fetched, the release is pinned without them and kitew checks downloads against the list the release serves.
