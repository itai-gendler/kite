---
appliesTo:
- type: entity
  id: account
  effect: changes
  facts: [Email, Picture]
  contexts:
  - place: studio
permits:
- actors: [owner]
  when:
  - {entity: studio-server, fact: Changes allowed, is: true}
references:
- kind: code
  role: implementation
  target: internal/api/account.go#handleUpdateProfile
- kind: code
  role: implementation
  target: internal/api/account.go#handleUploadAvatar
---

# Only the owner changes the profile kept with the account

The email and picture shown in the studio are the owner's to change, where the server allows changes.
