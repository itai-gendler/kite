---
appliesTo:
- type: capability
  id: set-up-site
- type: capability
  id: set-password
- type: capability
  id: change-sign-in
references:
- kind: code
  role: implementation
  target: internal/auth/account.go
---

# A password has at least 8 characters

Length is all that is asked for.
