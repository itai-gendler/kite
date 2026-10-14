---
availability:
- place: studio::signed-in
- place: cli
domain: deploy
references:
- kind: code
  role: implementation
  target: internal/api/kite.go#handlePin
- kind: code
  role: implementation
  target: internal/cli/wrapper_cmd.go#newWrapperCmd
- kind: code
  role: implementation
  target: internal/kitew/kitew.go
---

# Pin the Kite release

Record in kite.lock the Kite release the site builds with, so kitew and the deploy workflow build with the Kite the owner previewed with: Pin, Build with the running release, or Add the checksums on the Deploy screen; `kite wrapper` pins the running release or the one --version names and writes kitew and kitew.ps1 too. The pin reaches the deploy once kite.lock is published.
