---
appliesTo:
- type: capability
  id: sign-in
- type: capability
  id: change-sign-in
- type: capability
  id: remove-password
references:
- kind: code
  role: implementation
  target: internal/auth/throttle.go
- kind: code
  role: implementation
  target: internal/api/auth.go#failThrottled
---

# Failed password attempts are limited

After several failures, signing in and confirming the current password are refused for a while, with how long to wait; a wrong user name and a wrong password get the same answer.
