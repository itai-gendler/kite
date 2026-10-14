---
kind: primary
routes:
  cli: Command line
steps:
- text: The Owner runs kite init blog and answers what the site is called, their name, where it will live
    and its language
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Owner says whether to write the GitHub deploy workflow, tell Explore after each deploy, start
    a git repository and set a password now
  kind: actor
  actor: owner
  entities: []
  contexts:
    cli:
      place: cli
- text: The Product writes kite.yaml, the deploy workflows, kitew with the running release pinned, and
    the starting folders
  kind: product
  actor: owner
  entities:
  - {entity: site-settings, effect: changes, facts: [Title, Address, Language, Author, Update services,
      Pinned Kite release]}
  contexts:
    cli:
      place: cli
references:
- kind: code
  role: implementation
  target: internal/cli/init_cmd.go#newInitCmd
- kind: code
  role: implementation
  target: internal/cli/init_cmd.go#create
---

# Create a site with kite init

## Trigger

The Owner starts a site from a terminal.

## Outcome

The project is ready to serve; its studio works in local mode until a password is set.

## Edge cases

- Every answer has a flag, and --yes or a run with no terminal takes the defaults without asking.
- A folder that already holds kite.yaml is refused before anything is asked.
- A password given now is stored as the account admin; a Kite built from source pins no release.
