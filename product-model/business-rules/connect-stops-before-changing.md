---
appliesTo:
- type: capability
  id: connect-github
  contexts:
  - place: studio::signed-in
  - place: cli
references:
- kind: code
  role: implementation
  target: internal/publish/git/connect.go#ConnectGitHub
---

# Connecting GitHub stops before changing anything it should not change

Everything that could refuse is asked first — a token GitHub does not take, a repository it cannot see, one with commits while the site has none, an origin that points elsewhere, a site inside another repository — so a connect that stops has changed nothing.
