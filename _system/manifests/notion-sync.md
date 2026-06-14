---
type: System Manifest
title: Public Notion Sync Model
description: How Knowledge Atlas relates to Notion, Obsidian, and GitHub Pages.
visibility: public
status: active
tags:
  - notion
  - sync
  - github
  - okf
---

# Public Notion sync model

Notion may mirror public Knowledge Atlas metadata.

It is not the canonical source of public content.

## Roles

```text
Git/Markdown   = canonical public content
GitHub Pages   = public website
Obsidian       = local editor
Notion         = cockpit, database UI, workflow mirror
```

## Notion `OKF Notes` database

Each row may represent one public Markdown file.

Properties:

```text
Title
OKF ID
Type
Visibility
Status
Curation
Tags
Resource URL
Git Path
Repo
GitHub Source URL
GitHub Pages URL
Obsidian URI
Last Synced
Conflict Status
```

## Public links

Public Notion rows may store:

- GitHub source URL
- GitHub Pages URL
- public resource URL

Avoid storing private Obsidian URIs in public-facing Notion areas.

## Sync direction

Initial sync:

```text
Git/OKF → Notion
```

Later optional sync:

```text
Notion status fields → Git frontmatter
```

Full Notion body sync should be avoided until conflict handling exists.

## Sync key

Use stable IDs.

Example:

```yaml
id: atlas:concept:context-engineering
```

Do not rely only on titles or paths.

## GitHub Pages

GitHub Pages renders the public repo.

It is not a source of truth.
