---
appliesTo:
- type: entity
  id: plugin
  effect: changes
  to: 'On'
  contexts:
  - place: studio
permits:
- actors: [owner]
  when:
  - {entity: studio-server, fact: Changes allowed, is: true}
  - {fact: Problem, absent: true}
references:
- kind: code
  role: implementation
  target: internal/api/plugins.go#handleSwitchPlugin
---

# Only a plugin that loads and passes its check is switched on

A plugin that cannot be used — it does not load, or fails the check it is given before it is turned on — stays off.
