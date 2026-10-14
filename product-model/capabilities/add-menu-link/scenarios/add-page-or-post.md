---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner chooses Add a page or post and picks a published page by its title
  kind: actor
  actor: owner
  entities:
  - {entity: page, effect: reads, facts: [Title]}
  - {entity: post, effect: reads, facts: []}
  contexts:
    studio:
      place: studio::signed-in::menus
- text: The Product adds a link with the page's title and its address
  kind: product
  actor: owner
  entities:
  - {entity: page, effect: reads, facts: [Title, Slug]}
  - {entity: menu-link, effect: creates, facts: [Menu, Name, Address]}
  contexts:
    studio:
      place: studio::signed-in::menus
- text: The Owner chooses Save
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::menus
references:
- kind: code
  role: implementation
  target: web/src/features/settings/menus/index.tsx
---

# Add a page or post to a menu

## Trigger

The Owner links a page without typing its address.

## Outcome

The menu holds a link to the page.
