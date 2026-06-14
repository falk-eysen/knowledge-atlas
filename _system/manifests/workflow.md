---
type: System Manifest
title: Public Knowledge Workflow
description: Workflow for publishing curated knowledge into Knowledge Atlas.
visibility: public
status: active
tags:
  - workflow
  - publication
  - okf
---

# Public knowledge workflow

Knowledge Atlas is the public publication layer.

It receives curated material from reviewed private workspaces.

## Workflow

```text
private capture
  ↓
private raw source
  ↓
private synthesis
  ↓
public candidate
  ↓
reviewed public draft
  ↓
pull request
  ↓
merge
  ↓
GitHub Pages
```

## What this repo owns

Knowledge Atlas owns:

- public curated Markdown
- public references
- public concepts
- public claims
- public maps
- public playbooks
- public learning paths
- public Git history
- public rendered site

## What this repo does not own

Knowledge Atlas does not own:

- private source material
- private capture
- journal notes
- work-sensitive context
- Notion as canonical storage
- Obsidian as canonical storage

## Canonical content

The canonical public content is the Markdown in this Git repository.

GitHub Pages renders it through Quartz.

Notion may mirror metadata and links.

Obsidian may edit files locally.

## Site build

The public site is built from reviewed public sections only:

- `index.md`
- `README.md`
- `map.md`
- `_wiki/`
- `_system/manifests/`
- `_outputs/`, when public deliverables exist

The site build excludes raw capture, archives, scripts, local editor state, and private/draft filename patterns.

## Publishing rule

Nothing enters this repo from private material without review.

## Good public pages

Good public pages are:

- clear
- cited
- safe
- durable
- useful
- linked
- not over-personal
- not hype-driven
