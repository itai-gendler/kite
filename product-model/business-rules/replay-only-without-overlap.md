---
appliesTo:
- type: capability
  id: push-commits
  contexts:
  - place: studio::signed-in
  - place: cli
references:
- kind: code
  role: implementation
  target: internal/publish/git/remote.go#remoteChange
- kind: code
  role: implementation
  target: internal/publish/git/remote.go#replay
---

# A commit is put on top of the remote's only when the remote changed none of its files

The one unpushed commit is replayed on top of a remote that moved on only when none of the remote's new commits change a file it changed, the branch and the remote share history, and the files the remote changed have no uncommitted changes here.
