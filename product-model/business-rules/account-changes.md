---
appliesTo:
- type: entity
  id: account
  effect: changes
  facts: [User name, Password]
  contexts:
  - place: studio
permits:
- actors: [owner]
  when:
  - {entity: studio-server, fact: Changes allowed, is: true}
  - {fact: Comes from, is: studio}
references:
- kind: code
  role: implementation
  target: internal/api/account.go#handleSetCredentials
- kind: code
  role: implementation
  target: internal/auth/keeper.go#changeable
---

# Only the owner changes the sign-in of an account the studio keeps

An account given by the server's environment is changed only where it is set; one the studio keeps is changed by the owner, after confirming the current password where it guards sign-in, on a server that allows changes.
