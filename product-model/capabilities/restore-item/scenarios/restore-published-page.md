---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner restores a page from the trash
  kind: actor
  actor: owner
  entities:
  - {entity: page, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::content-list
- text: The Product takes the page out of the trash, published as it was
  kind: product
  actor: owner
  entities:
  - {entity: page, effect: changes, from: In the trash, to: Published, facts: [Deleted at]}
  contexts:
    studio:
      place: studio::signed-in::content-list
references:
- kind: code
  role: implementation
  target: internal/store/file/writer.go
---

# Restore a published page

## Trigger

The Owner wants a deleted page back.

## Outcome

The page is published again and returns to the site once built.
