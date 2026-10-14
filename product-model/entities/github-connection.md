---
references:
- kind: code
  role: implementation
  target: internal/publish/github.go#GitHubState
- kind: code
  role: implementation
  target: internal/publish/git/connect.go#ConnectGitHub
- kind: doc
  role: intent
  target: docs/design/github.md
---

# GitHub connection

The link between the site and a repository on GitHub, made with a fine-grained token for that repository alone.

## Information kept

- **Repository** — owner/name of the repository its remote points to
- **Token** — the token, kept on the server readable by it alone and never shown again
- **Token comes from** — kept by the studio, or given by KITE_GITHUB_TOKEN, which wins
- **GitHub account** — the account the token belongs to, which makes commits where git has no identity of its own
- **Pages address** — where GitHub Pages serves the site, once connecting turned it on
