---
actors:
- visitor
access: public
entryPoints:
- studio: /admin/sign-in
- studio: /admin/setup
references:
- kind: code
  role: implementation
  target: web/src/routes/(auth)/sign-in.tsx
- kind: code
  role: implementation
  target: web/src/routes/(auth)/setup.tsx
- kind: code
  role: implementation
  target: internal/api/auth.go#publicPaths
- kind: code
  role: implementation
  target: internal/api/setup.go#setupPaths
---

# Signed out

Where someone who has not signed in reaches the studio: the sign-in form of a
studio guarded by a password, and the setup of a server nobody has configured
yet or of a new site in an empty folder.
