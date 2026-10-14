---
appliesTo:
- type: capability
  id: change-sign-in
- type: capability
  id: sign-out-other-browsers
- type: capability
  id: remove-password
references:
- kind: code
  role: implementation
  target: internal/auth/keeper.go#changeable
---

# An account from the environment is changed only where it is set

KITE_ADMIN_USER with KITE_ADMIN_PASSWORD or KITE_ADMIN_PASSWORD_HASH wins over the stored account; the studio cannot change, rotate or remove it.
