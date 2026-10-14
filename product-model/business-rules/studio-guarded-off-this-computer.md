---
appliesTo:
- type: context
  context:
    place: studio::signed-in
- type: capability
  id: set-up-site
references:
- kind: code
  role: implementation
  target: internal/serve/server.go#NewWithClock
- kind: code
  role: implementation
  target: internal/api/auth.go#allow
---

# Anywhere but this computer the studio needs an account, and until it has one only setup answers

A studio on this computer with no password works in local mode, without a sign-in. A server reachable from other machines with no account answers nothing but its setup — not the content, the drafts or the settings — and does not start at all without changes allowed.
