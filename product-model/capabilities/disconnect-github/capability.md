---
availability:
- place: studio::signed-in
- place: cli
domain: deploy
references:
- kind: code
  role: implementation
  target: internal/api/github.go#handleDisconnectGitHub
- kind: code
  role: implementation
  target: internal/cli/github_cmd.go#newGitHubDisconnectCmd
---

# Disconnect GitHub

Forget the token the server keeps for GitHub (Disconnect, or `kite github disconnect`). The remote stays, and pushing goes back to whatever credentials git has; a token KITE_GITHUB_TOKEN gives is taken out of the environment instead.
