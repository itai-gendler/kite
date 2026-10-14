---
references:
- kind: code
  role: implementation
  target: internal/auth/session.go
---

# Session

One browser signed in to the studio.

## Information kept

- **Expires** — when the browser has to sign in again
- **Remembered** — whether it stays signed in after the browser closes (Keep me signed in)
