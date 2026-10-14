---
appliesTo:
- type: capability
  id: connect-github
- type: capability
  id: disconnect-github
- type: entity
  id: github-connection
references:
- kind: doc
  role: intent
  target: docs/design/github.md
- kind: code
  role: implementation
  target: internal/publish/git/git.go
---

# The GitHub token is never shown again and goes only to github.com

It is kept on the server readable by its owner alone, or given by KITE_GITHUB_TOKEN, which wins; it is used for pushes over https to github.com and for questions about deployments, and git receives it through its environment, never in a file or a command's arguments.
