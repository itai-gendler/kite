---
availability:
- place: studio::signed-in
- place: cli
domain: account
references:
- kind: code
  role: implementation
  target: internal/api/account.go#handleRemoveCredentials
- kind: code
  role: implementation
  target: internal/auth/keeper.go#Remove
- kind: code
  role: implementation
  target: internal/cli/auth_cmd.go#newAuthRemoveCmd
---

# Remove the password

Take the password away so the studio on this computer goes back to local mode, without a sign-in (Remove password on the Account page, or `kite auth remove`).
