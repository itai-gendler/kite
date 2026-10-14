---
appliesTo:
- type: capability
  id: publish-items
  contexts:
  - place: studio::signed-in
  - place: cli
references:
- kind: code
  role: implementation
  target: internal/publish/git/preflight.go#preflight
- kind: code
  role: implementation
  target: internal/api/publish.go#handlePublish
---

# A publish stops before committing whenever the repository is in a state Kite does not understand

Every problem — git missing, not a repository, a submodule, a detached HEAD, an operation in progress, git-lfs missing, a file over 100 MB — is reported at once before anything is committed; warnings are shown and acknowledged first.
