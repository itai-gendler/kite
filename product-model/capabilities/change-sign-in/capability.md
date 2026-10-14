---
availability:
- place: studio::signed-in
- place: cli
domain: account
references:
- kind: code
  role: implementation
  target: internal/api/account.go#handleSetCredentials
- kind: code
  role: implementation
  target: internal/auth/keeper.go#Change
---

# Change the sign-in

Change the user name, the password or both once the current password is confirmed (Update sign-in, or `kite auth set-password` on a site that has an account). Every other browser is signed out; this one stays.
