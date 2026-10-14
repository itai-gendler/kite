---
appliesTo:
- type: entity
  id: commit
  effect: creates
  contexts:
  - place: studio
permits:
- actors: [owner]
  when:
  - {entity: studio-server, fact: Changes allowed, is: true}
  - {entity: site-settings, fact: Publisher, is: git}
references:
- kind: code
  role: implementation
  target: internal/api/publish.go#publishRequest
- kind: code
  role: implementation
  target: internal/site/site.go#newPublisher
---

# Only the owner publishes, where the site publishes with Git and the server allows changes

Publishing and connecting GitHub commit only on a server that allows changes, for a site whose publisher is git; a site set to publish with none leaves committing to its owner.
