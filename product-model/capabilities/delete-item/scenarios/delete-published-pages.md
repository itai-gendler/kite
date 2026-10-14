---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner selects published pages in the list, chooses Delete and confirms
  kind: actor
  actor: owner
  entities:
  - {entity: page, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::content-list
- text: The Product moves each selected page to the trash
  kind: product
  actor: owner
  entities:
  - {entity: page, effect: changes, from: Published, to: In the trash, facts: [Deleted at]}
  contexts:
    studio:
      place: studio::signed-in::content-list
references:
- kind: code
  role: implementation
  target: web/src/features/contents/index.tsx
---

# Delete published pages from the list

## Trigger

The Owner clears out pages the site no longer needs.

## Outcome

The pages are in the trash and leave the site once it is built; the list says how many were deleted.

## Edge cases

- When some of the selection could not be deleted, the list says how many were and how many failed, and asks for a refresh before trying again.
