---
appliesTo:
- type: entity
  id: declared-content
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
  target: internal/api/write.go#writable
---

# Only the owner changes declared content, where the server allows changes

In the studio this is offered to the owner only while the server was started with changes allowed.
