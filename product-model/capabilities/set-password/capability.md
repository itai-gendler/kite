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
  target: internal/auth/keeper.go#Create
- kind: code
  role: implementation
  target: internal/cli/auth_cmd.go#newAuthSetPasswordCmd
---

# Set a password

Give a studio in local mode a password; it asks for it from that moment, without a restart (Settings → Account, Set password, or `kite auth set-password`).
