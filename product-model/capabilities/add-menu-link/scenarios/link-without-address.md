---
kind: validation
routes:
  studio: Studio
steps:
- text: 'The Owner adds a link whose address starts with none of https://, http://, mailto:, tel: or a
    slash, and saves'
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::menus
- text: The Product refuses the save and names the link
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::menus
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#checkMenu
---

# Add a link with an address that is not one

## Trigger

The address is malformed.

## Outcome

kite.yaml is unchanged.
