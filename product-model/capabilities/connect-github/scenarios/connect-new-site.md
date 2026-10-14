---
kind: primary
routes:
  studio: Studio
steps:
- text: The Owner gives the repository as owner/name and a token, leaves the GitHub hosting option on,
    and chooses Connect
  kind: actor
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product asks GitHub everything that could refuse before changing anything
  kind: product
  actor: owner
  entities: []
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product keeps the token on the server, starts a repository, adds origin and writes the deploy
    workflows
  kind: product
  actor: owner
  entities:
  - {entity: github-connection, effect: creates, facts: [Repository, Token, Token comes from, GitHub account,
      Pages address]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product commits the site's own content and settings as "Start the site", turns GitHub hosting
    on and pushes
  kind: product
  actor: owner
  entities:
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
- kind: code
  role: implementation
  target: internal/publish/git/connect.go#committable
---

# Connect a new site with GitHub Pages

## Trigger

The Owner wants the site on GitHub Pages without a terminal.

## Outcome

The Deploy page lists what was done and where the site will be once the first deploy finishes; from now on publishing pushes with the token.

## Edge cases

- Where git has no identity of its own, as in a container, commits are made by the connected account at its noreply address.
- A remote over ssh keeps using ssh.
