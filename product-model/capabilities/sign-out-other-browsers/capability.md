---
availability:
- place: studio::signed-in
domain: account
references:
- kind: code
  role: implementation
  target: internal/api/account.go#handleEndSessions
- kind: code
  role: implementation
  target: internal/auth/keeper.go#Rotate
---

# Sign out other browsers

End every session but this browser's without changing how anybody signs in (Sign out other browsers on the Account page).
