---
appliesTo:
- type: entity
  id: github-connection
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
  target: internal/api/github.go#githubOf
---

# Only the owner connects GitHub, where the site publishes with Git and the server allows changes

Connecting is offered by a site whose publisher is git, on a server that allows changes.
