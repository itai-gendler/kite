---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner renames a link and puts two links under it, and chooses Save
  kind: actor
  actor: owner
  entities:
  - {entity: menu-link, effect: reads, facts: [Name, Links under it]}
  contexts:
    studio:
      place: studio::signed-in::menus
- text: The Product writes the menu to kite.yaml
  kind: product
  actor: owner
  entities:
  - {entity: menu-link, effect: changes, facts: [Name, Links under it]}
  contexts:
    studio:
      place: studio::signed-in::menus
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#storedMenu
---

# Change a menu link

## Trigger

The Owner reorganizes the header.

## Outcome

The theme draws the changed link and its submenu.

## Edge cases

- Links written deeper than the theme draws are still shown on the Menus screen, so none is hidden.
