---
kind: primary
routes:
  studio: Studio
steps:
- text: A pushed commit is waiting to be deployed and the site has a public address
  kind: condition
  unattended: true
  entities:
  - {entity: commit, effect: reads, facts: [Hash]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product reads kite-build.json from the site each minute
  kind: product
  entities:
  - {entity: site-settings, effect: reads, facts: [Address, Build stamp]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The site was built from the commit, or from a later commit that contains it
  kind: condition
  entities:
  - {entity: commit, effect: reads, facts: [Hash]}
  contexts:
    studio:
      place: studio::signed-in::deploy
- text: The Product marks the commit live at the site's address
  kind: product
  entities:
  - {entity: commit, effect: changes, from: Pushed, to: Live, facts: [Live address]}
  contexts:
    studio:
      place: studio::signed-in::deploy
references:
- kind: code
  role: implementation
  target: internal/publish/git/site.go#publicAddress
- kind: code
  role: implementation
  target: internal/stamp/stamp.go
---

# The site says the commit is live

## Trigger

A commit was pushed to a repository whatever host builds.

## Outcome

The panel says the site is up to date. This works for any host, a server of one's own included, and needs no account.

## Edge cases

- An address readers cannot reach — localhost, a private address, example.com — is not asked.
- A site with build.stamp off writes no kite-build.json, so only the host can answer.
