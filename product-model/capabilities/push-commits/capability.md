---
availability:
- place: studio::signed-in
- place: cli
references:
- kind: code
  role: implementation
  target: internal/api/publish.go#handlePush
- kind: code
  role: implementation
  target: internal/publish/git/remote.go#Push
- kind: code
  role: implementation
  target: internal/publish/git/remote.go#replay
---

# Push commits

Send commits already made to the remote: after a push that failed, with Push N commits on the dashboard, Push again in the publishing panel, or `kite publish --push`. When the remote has moved on without touching what the one unpushed commit changed, Put mine on top and push (or `--rebase`) replays the commit on top of the remote's commits first.
