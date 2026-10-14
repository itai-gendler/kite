---
appliesTo:
- type: entity
  id: site-settings
  effect: changes
  contexts:
  - place: studio
permits:
- actors: [owner]
  when:
  - {entity: studio-server, fact: Changes allowed, is: true}
- actors: [visitor]
  when:
  - {entity: studio-server, fact: Waiting for setup, is: true}
references:
- kind: code
  role: implementation
  target: internal/api/settings.go#handleUpdateSettings
- kind: code
  role: implementation
  target: internal/api/setup.go#handleSetup
---

# Only the owner changes the site's settings, or a visitor finishing setup

The owner changes kite.yaml and kite.lock where the server allows changes. While a server waits for its setup, the setup form — the one thing such a server answers — writes the site's description.
