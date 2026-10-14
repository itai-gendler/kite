---
appliesTo:
- type: entity
  id: account
  effect: removes
  contexts:
  - place: studio
permits:
- actors: [owner]
  when:
  - {entity: studio-server, fact: Changes allowed, is: true}
  - {fact: Comes from, is: studio}
  - {entity: studio-server, fact: Reachable from other machines, is: false}
references:
- kind: code
  role: implementation
  target: internal/auth/keeper.go#Remove
- kind: code
  role: implementation
  target: internal/api/account.go#handleRemoveCredentials
---

# Only the owner removes the password, and only on a server this computer alone can reach

A server reachable from other machines keeps its password. An account given by the environment cannot be removed in the studio.
