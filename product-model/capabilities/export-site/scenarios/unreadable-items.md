---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner chooses Export zip
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: Some content could not be read into the index
  kind: condition
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product refuses to build and says what stopped it
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
references:
- kind: code
  role: implementation
  target: internal/api/export.go#handleExport
---

# Export a site with items that cannot be read

## Trigger

The site has content the index refused.

## Outcome

No zip is made until the content is fixed.
