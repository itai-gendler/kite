---
kind: validation
routes:
  studio: Studio
steps:
- text: The Owner chooses Connect
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: GitHub does not take the token, cannot see the repository, the repository has history while the
    site has none, origin points elsewhere, or the site sits inside another repository
  kind: condition
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product stops before changing anything and says why
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
references:
- kind: code
  role: implementation
  target: internal/publish/git/connect.go#ConnectGitHub
---

# Connect refused

## Trigger

Connecting would have to change something it should not.

## Outcome

The project is as it was.

## Edge cases

- With KITE_GITHUB_TOKEN set, a token given here is refused: the environment's wins.
