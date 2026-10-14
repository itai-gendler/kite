---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner tries to remove the password of a server reachable from other machines
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::account
- text: 'The Product refuses: other machines can reach this server, so its studio keeps a password'
  kind: product
  actor: owner
  entities:
  - {entity: studio-server, effect: reads, facts: [Reachable from other machines]}
  contexts:
    studio:
      place: studio::signed-in::account
references:
- kind: code
  role: implementation
  target: internal/auth/keeper.go#Remove
---

# Remove the password of a reachable server

## Trigger

The server listens beyond this computer.

## Outcome

The password stays.
