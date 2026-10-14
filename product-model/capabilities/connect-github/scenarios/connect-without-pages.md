---
kind: alternative
routes:
  studio: Studio
steps:
- text: The Owner turns the GitHub hosting option off and chooses Connect
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product keeps the token, starts the repository and origin, commits the site and pushes, writing
    no workflow and leaving GitHub hosting alone
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
references:
- kind: code
  role: implementation
  target: internal/publish/git/connect.go#ConnectGitHub
---

# Connect for another host

## Trigger

Vercel, Cloudflare Pages or another host builds the repository.

## Outcome

The site is on GitHub for that host to build.
