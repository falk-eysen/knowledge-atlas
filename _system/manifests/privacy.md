---
type: System Manifest
title: Public Privacy Rules
description: Safety rules for preventing private leakage into Knowledge Atlas.
visibility: public
status: active
tags:
  - privacy
  - publication
  - safety
---

# Public privacy rules

This repository is public.

Assume every committed file may be read by:

- strangers
- coworkers
- employers
- recruiters
- collaborators
- search engines
- future AI systems

## Forbidden content

Do not commit:

- credentials
- tokens
- private keys
- passwords
- internal hostnames
- IP addresses
- customer identifiers
- workplace-sensitive details
- private Notion links
- private Obsidian links
- private local filesystem paths
- journal notes
- salary notes
- health notes
- private people notes
- unredacted screenshots
- personal data without explicit reason

## Forbidden references

Do not link to:

```text
private repo names
_private
private vault paths
private Notion pages
private Obsidian URIs
```

## Required visibility

Public files should say:

```yaml
visibility: public
```

Do not commit:

```yaml
visibility: private
```

## Publication test

Before committing, ask:

```text
Would this be safe and useful if read by a stranger?
```

If not, do not publish it.

## Redaction

When transforming private knowledge into public knowledge:

- remove personal context
- remove workplace-sensitive details
- remove identifying information
- replace examples with generic examples
- cite public sources
- keep uncertainty visible
