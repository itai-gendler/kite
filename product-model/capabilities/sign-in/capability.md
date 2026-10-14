---
availability:
- place: studio::signed-out
references:
- kind: code
  role: implementation
  target: internal/api/auth.go#handleLogin
- kind: code
  role: implementation
  target: internal/auth/guard.go
---

# Sign in

Sign in to a studio that has a password, with its user name and password, optionally kept after the browser closes.
