---
appliesTo:
- type: entity
  id: commit
  effect: changes
  contexts:
  - place: studio
permits:
- actors: [owner]
  when:
  - {entity: studio-server, fact: Changes allowed, is: true}
  - {entity: site-settings, fact: Publisher, is: git}
- unattended: true
references:
- kind: code
  role: implementation
  target: internal/api/publish.go#handlePush
- kind: code
  role: implementation
  target: internal/publish/git/publisher.go#deployed
---

# Only the owner pushes a commit, and only the Product marks how its deployment went

The owner pushes and replays commits where the site publishes with Git and the server allows changes. Whether a pushed commit is deploying, live or failed is what the Product finds out on its own from the site and the host.
