---
appliesTo:
- type: context
  context:
    place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/api/auth.go#allow
- kind: code
  role: implementation
  target: internal/api/auth.go#publicPaths
---

# The studio asks for a sign-in whenever the site has an account

Every request but the setup, the sign-in and the API's own description needs a session once an account exists.
