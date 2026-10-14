---
appliesTo:
- type: entity
  id: account
  effect: creates
  contexts:
  - place: studio
permits:
- actors: [visitor]
  when:
  - {entity: studio-server, fact: Waiting for setup, is: true}
- actors: [owner]
  when:
  - {entity: studio-server, fact: Changes allowed, is: true}
references:
- kind: code
  role: implementation
  target: internal/api/setup.go#handleSetup
- kind: code
  role: implementation
  target: internal/auth/keeper.go#Create
---

# Only a visitor finishing setup, or the owner of an open studio, creates the account

The account is created by finishing the setup of a server that waits for it, or by the owner setting a password in a studio that has none, where the server allows changes.
