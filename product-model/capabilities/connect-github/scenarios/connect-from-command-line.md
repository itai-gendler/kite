---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner runs kite github connect owner/name and gives the token when asked
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product connects as the studio does, printing each step
  kind: product
  actor: owner
  entities:
  - {entity: github-connection, effect: creates, facts: [Repository, Token, Token comes from, GitHub account,
      Pages address]}
  - {entity: commit, effect: creates, to: Committed, facts: [Message, Paths, Branch, Hash]}
  contexts:
    cli:
      place: cli
- text: The push reaches GitHub
  kind: product
  actor: owner
  entities:
  - {entity: commit, effect: changes, from: Committed, to: Pushed, facts: [Remote]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/github_cmd.go#newGitHubConnectCmd
---

# Connect from the command line

## Trigger

The Owner connects from a terminal.

## Outcome

The site is connected and pushed.

## Edge cases

- --stdin reads the token from standard input; with KITE_GITHUB_TOKEN set nothing is asked.
