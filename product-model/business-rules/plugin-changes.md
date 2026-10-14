---
appliesTo:
- type: entity
  id: plugin
  effect: changes
  contexts:
  - place: studio
permits:
- actors: [owner]
  when:
  - {entity: studio-server, fact: Changes allowed, is: true}
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleSwitchPlugin
---

# Only the owner switches, configures, replaces or updates a plugin, where the server allows changes

In the studio this is offered to the owner only while the server was started with changes allowed (--write, on for kite run); a server without it reads and previews, and refuses the change. The command line changes the site's files directly.
