---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner adds a link named About with the address /about/ to the header menu and chooses Save
  kind: actor
  actor: owner
  entities:
  - {entity: theme, effect: reads, facts: [Menus it draws]}
  contexts:
    studio:
      place: studio::signed-in::menus
- text: The Product checks the link and writes the menu to kite.yaml
  kind: product
  actor: owner
  entities:
  - {entity: menu-link, effect: creates, facts: [Menu, Name, Address]}
  contexts:
    studio:
      place: studio::signed-in::menus
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#handleUpdateSettings
---

# Add a link to the header

## Trigger

The Owner wants a link across the top of every page.

## Outcome

The theme draws the link; another theme that draws the same menu finds it too.
