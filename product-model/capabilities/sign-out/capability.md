---
availability:
- place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/api/auth.go#handleLogout
- kind: code
  role: implementation
  target: web/src/components/layout/nav-user.tsx
---

# Sign out

Sign this browser out of a studio that has a password. A studio in local mode has nothing to sign out of.
