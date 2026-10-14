---
kind: edge
routes:
  studio: Studio
steps:
- text: The Owner chooses Connect with the GitHub hosting option on
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product connects, commits and pushes
  kind: product
  actor: owner
  entities:
  - {entity: github-connection, effect: creates, facts: [Repository, Token, Token comes from, GitHub account]}
  - {entity: commit, effect: creates, to: Committed, facts: [Message, Paths, Branch, Hash]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The push reaches GitHub
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: changes, from: Committed, to: Pushed, facts: [Remote]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: GitHub will not turn its hosting on, even after the push
  kind: condition
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

# Connect when Pages will not turn on

## Trigger

GitHub refuses Pages for the repository.

## Outcome

The connection stands, and a warning says Pages was not turned on.
