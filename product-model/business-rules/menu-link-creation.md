---
appliesTo:
- type: entity
  id: menu-link
  effect: creates
  contexts:
  - place: studio
permits:
- actors: [owner]
  when:
  - {entity: studio-server, fact: Changes allowed, is: true}
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#handleUpdateSettings
---

# Only the owner adds a menu link, where the server allows changes

Menus are written to kite.yaml through the settings, which change only where the server allows changes.
