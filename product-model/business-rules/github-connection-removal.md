---
appliesTo:
- type: entity
  id: github-connection
  effect: removes
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
  target: internal/api/github.go#handleDisconnectGitHub
---

# Only the owner disconnects GitHub, where the site publishes with Git and the server allows changes

Disconnecting forgets the kept token on a server that allows changes.
