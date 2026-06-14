---
type: System Document
title: Repository Map
description: Top-level map of the public Knowledge Atlas.
visibility: public
status: active
tags:
  - map
  - repository
  - okf
---

# Repository map

This repository is a public OKF-compatible knowledge atlas.

## Current root

```text
.
├── README.md
├── CONTRIBUTING.md
├── AGENTS.md
├── map.md
├── index.md
├── _raw/
│   ├── web/
│   ├── papers/
│   ├── repos/
│   ├── books/
│   ├── videos/
│   └── reference/
├── _wiki/
│   ├── index.md
│   ├── log.md
│   ├── concepts/
│   ├── references/
│   ├── claims/
│   ├── maps/
│   ├── projects/
│   ├── areas/
│   ├── themes/
│   ├── open_questions/
│   ├── playbooks/
│   ├── patterns/
│   └── learning_paths/
├── _outputs/
│   ├── reports/
│   ├── guides/
│   └── slides/
├── _system/
│   ├── manifests/
│   ├── templates/
│   ├── prompts/
│   ├── lint/
│   └── indexes/
├── _archive/
└── scripts/
```

## Layer model

| Layer | Purpose |
|---|---|
| `_raw/` | Public-safe source notes |
| `_wiki/` | Curated public knowledge |
| `_outputs/` | Public deliverables |
| `_system/` | Schema, templates, manifests, workflows |
| `_archive/` | Retired public material |
| `scripts/` | Helper automation |

## Quick navigation

| I want to... | Start here |
|---|---|
| Understand the repo | `README.md`, `map.md`, `AGENTS.md` |
| Browse knowledge | `_wiki/index.md` |
| Check history | `_wiki/log.md` |
| Understand OKF profile | `_system/manifests/okf-profile.md` |
| Understand workflow | `_system/manifests/workflow.md` |
| Understand privacy rules | `_system/manifests/privacy.md` |
| Understand Notion sync | `_system/manifests/notion-sync.md` |
| Add a reference | `_system/templates/reference.md` |
| Add a concept | `_system/templates/concept.md` |
| Add a claim | `_system/templates/claim.md` |
| Add a map | `_system/templates/map.md` |
| Add a playbook | `_system/templates/playbook.md` |

## Public safety

This repo is public.

Do not add private source paths, private Notion links, private Obsidian links, work-sensitive material, or personal data.
