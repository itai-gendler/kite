---
availability:
- place: studio::signed-in
domain: account
references:
- kind: code
  role: implementation
  target: internal/api/account.go#handleUploadAvatar
- kind: code
  role: implementation
  target: internal/auth/profile.go
---

# Change the picture

Upload or change the picture the studio shows for the owner (Upload picture, Change picture on the Account page). It is kept on the server, cropped to a square and scaled to 256 pixels, and never published.
