---
type: System Document
title: Knowledge Atlas
description: Public curated OKF-style knowledge catalog.
visibility: public
status: active
tags:
  - knowledge-atlas
  - okf
  - public
---

# Knowledge Atlas

This is my public knowledge atlas.

It is a curated, OKF-compatible knowledge catalog for concepts, references, claims, maps, patterns, projects, playbooks, and learning paths.

It is not my private second brain.

Reviewed material may come from a separate private workspace, but private source paths and identifiers stay out of this repository.

## Purpose

This repo exists to publish durable knowledge that may be useful to others.

It contains:

- concepts
- references
- claims
- maps
- playbooks
- patterns
- learning paths
- public project notes

It does not contain:

- private journal notes
- private work context
- personal people notes
- salary notes
- health notes
- credentials
- customer data
- internal infrastructure details
- private source material

## Repository model

```text
_raw/      public-safe source notes and references
_wiki/     curated public knowledge
_outputs/  public deliverables
_system/   schema, templates, manifests, workflows
_archive/  retired public material
scripts/   helper automation
```

## Public/private rule

This repo must never link to the private repo.

Allowed:

```text
public note → public source
public note → public note
public note → external source
```

Forbidden:

```text
public note → private note
public note → private source path
public note → private Obsidian URI
public note → private Notion page
```

## Main entry points

- [`index.md`](index.md) — OKF bundle entry
- [`map.md`](map.md) — repository map
- [`AGENTS.md`](AGENTS.md) — agent operating rules
- [`_wiki/index.md`](_wiki/index.md) — public knowledge index
- [`_wiki/log.md`](_wiki/log.md) — update log
- [`_system/manifests/okf-profile.md`](_system/manifests/okf-profile.md) — local OKF profile
- [`_system/manifests/workflow.md`](_system/manifests/workflow.md) — publication workflow
