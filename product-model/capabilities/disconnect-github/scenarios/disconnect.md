---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner chooses Disconnect on the Deploy screen
  kind: actor
  actor: owner
  entities:
  - {entity: github-connection, effect: reads, facts: [Repository, Token comes from]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product forgets the kept token
  kind: product
  actor: owner
  entities:
  - {entity: github-connection, effect: removes}
  contexts:
    studio:
      place: studio::signed-in::deploy
references:
- kind: code
  role: implementation
  target: internal/api/github.go#handleDisconnectGitHub
---

# Disconnect

## Trigger

The Owner no longer wants the server to hold a token.

## Outcome

No token is kept; the remote is left as it is.

## Edge cases

- A token from KITE_GITHUB_TOKEN stays in use; the studio says to take it out of the server's environment.
