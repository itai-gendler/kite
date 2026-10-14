---
kind: person
acts: external
relations:
- entity: account
  verb: signs in with
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: web/src/i18n/en.ts
- kind: doc
  role: context
  target: docs/design/architecture.md
---

# Owner

The person who owns the site: writes and publishes it, and runs it, in the studio and from the command line. The studio calls this one role Owner, in local mode as when signed in.
