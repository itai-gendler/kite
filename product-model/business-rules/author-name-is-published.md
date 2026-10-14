---
appliesTo:
- type: capability
  id: edit-profile
  contexts:
  - place: studio::signed-in
references:
- kind: code
  role: implementation
  target: internal/auth/profile.go#Profile
- kind: code
  role: implementation
  target: web/src/features/settings/account/index.tsx
---

# The owner's name is published as the site's author; the email and picture never are

The name lives in kite.yaml as site.author and reaches the site once published; the email and picture stay on the server in .kite/secrets.
