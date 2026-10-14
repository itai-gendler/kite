---
appliesTo:
- type: capability
  id: change-sign-in
- type: capability
  id: sign-out-other-browsers
references:
- kind: code
  role: implementation
  target: internal/auth/keeper.go#Change
- kind: code
  role: implementation
  target: internal/auth/keeper.go#Rotate
---

# Changing the sign-in signs out every other browser

The browser that made the change stays signed in.
