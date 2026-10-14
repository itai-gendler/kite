---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner removes a link from a menu and chooses Save
  kind: actor
  actor: owner
  entities:
  - {entity: menu-link, effect: reads, facts: [Name]}
  contexts:
    studio:
      place: studio::signed-in::menus
- text: The Product writes the menu without it
  kind: product
  actor: owner
  entities:
  - {entity: menu-link, effect: removes}
  contexts:
    studio:
      place: studio::signed-in::menus
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#checkMenu
---

# Remove a menu link

## Trigger

A link is no longer wanted.

## Outcome

The theme no longer draws the link.
