---
availability:
- place: studio::signed-in
domain: account
references:
- kind: code
  role: implementation
  target: web/src/features/settings/account/index.tsx
- kind: code
  role: implementation
  target: internal/api/account.go#handleUpdateProfile
- kind: code
  role: implementation
  target: internal/auth/profile.go#Profile
---

# Edit the profile

Change the owner's name — the site's author, kept in kite.yaml and published like any setting — and the email shown only in the studio (Save profile on the Account page).
