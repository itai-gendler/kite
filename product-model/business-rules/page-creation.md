---
appliesTo:
- type: entity
  id: page
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
  target: internal/api/write.go#writable
---

# Only the owner creates a page, where the server allows changes

In the studio this is offered to the owner only while the server was started with changes allowed (--write, on for kite run); a server without it reads and previews, and refuses the change. The command line changes the site's files directly.
