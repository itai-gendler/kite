---
availability:
- place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/commands.go#newDoctorCmd
- kind: doc
  role: intent
  target: docs/reference.md
  title: Moving from Hugo
---

# Check the project

`kite doctor` checks the project for problems: content it cannot read, items with no id, themes and plugins whose files no longer match what kite.lock records, and a Kite release other than the pinned one. With --fix-ids it gives every item without an id one, which is how a Hugo site's content opens in Kite.
