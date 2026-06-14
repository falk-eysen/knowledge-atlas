---
type: System Document
title: Agent Operating Schema
description: Operating instructions for agents working in the public Knowledge Atlas.
visibility: public
status: active
tags:
  - agents
  - workflow
  - public
---

# AGENTS.md

This file is the operating schema for agents working in this repository.

## Purpose

This is a public OKF-compatible knowledge catalog.

Agents should help keep it:

- public-safe
- cited
- navigable
- concise
- useful
- internally consistent
- OKF-compatible

## First read

When starting work, read:

1. [`map.md`](map.md)
2. [`index.md`](index.md)
3. [`_wiki/index.md`](_wiki/index.md)
4. relevant `_system/manifests/...`
5. relevant `_raw/...` source notes
6. relevant `_wiki/...` pages

## Repository model

```text
_raw/      public-safe source notes and references
_wiki/     curated public knowledge
_outputs/  public deliverables
_system/   manifests, templates, prompts, lint
_archive/  retired public material
scripts/   helper automation
```

## Placement rules

### `_raw/`

Use `_raw/` for public-safe source notes.

Examples:

- article notes
- paper notes
- public GitHub repository notes
- public video summaries
- book notes
- reference captures

Do not include private source material.

### `_wiki/`

Use `_wiki/` for synthesized public knowledge.

Examples:

- concepts
- claims
- maps
- areas
- themes
- projects
- open questions
- playbooks

Wiki pages should link to public sources.

### `_outputs/`

Use `_outputs/` for public deliverables.

Examples:

- reports
- guides
- slides
- public explanations

### `_system/`

Use `_system/` for repository rules, schemas, manifests, templates, and lint reports.

## Public boundary

This repo must never link to a private repo or vault.

Forbidden patterns:

```text
../<private-repo>
_private
visibility: private
private_refs
obsidian://open?vault=<private-vault>
```

## OKF conventions

Normal Markdown files require YAML frontmatter with `type`.

Recommended baseline:

```yaml
---
type: Concept
title: Example
description: One sentence.
visibility: public
status: draft
tags:
  - example
---
```

## Claim discipline

When a page makes a factual claim, prefer citations.

When uncertain, say so.

Do not overstate.

## Expected outcome

A good contribution leaves the atlas:

- easier to navigate
- safer to publish
- more useful to readers
- better cited
- more coherent
- still compatible with the OKF profile
