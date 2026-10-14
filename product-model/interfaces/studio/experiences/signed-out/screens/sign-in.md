---
entities:
- entity: account
  collects:
  - User name
  - Password
- entity: session
  collects:
  - Remembered
references:
- kind: code
  role: implementation
  target: web/src/features/auth/sign-in/index.tsx
---

# Sign in

Where the owner signs in to a studio that has a password.
