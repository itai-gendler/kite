---
availability:
- place: studio::signed-in
domain: account
references:
- kind: code
  role: implementation
  target: internal/api/account.go#handleRemoveAvatar
---

# Remove the picture

Take the owner's picture away; the studio goes back to their initials.
