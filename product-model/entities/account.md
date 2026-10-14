---
relations:
- entity: session
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: internal/auth/account.go
- kind: code
  role: implementation
  target: internal/auth/keeper.go#Keeper
- kind: code
  role: implementation
  target: internal/auth/profile.go#Profile
---

# Account

The one account that guards the studio. It is kept on the server, never committed, or given by the server's environment.

## Information kept

- **User name** — what the owner types to sign in
- **Password** — kept as an argon2id hash, at least 8 characters
- **Comes from** — studio, when the studio keeps it in .kite/secrets; environment, when the server's environment gives it (KITE_ADMIN_USER with KITE_ADMIN_PASSWORD or KITE_ADMIN_PASSWORD_HASH), which wins
- **Email** — shown only in the studio, never published
- **Picture** — shown only in the studio, never published
