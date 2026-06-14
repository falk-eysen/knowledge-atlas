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
│   │   └── index.md
│   ├── references/
│   │   └── index.md
│   ├── claims/
│   │   └── index.md
│   ├── maps/
│   │   └── index.md
│   ├── projects/
│   │   └── index.md
│   ├── areas/
│   │   └── index.md
│   ├── themes/
│   │   └── index.md
│   ├── open_questions/
│   │   └── index.md
│   ├── playbooks/
│   │   └── index.md
│   ├── patterns/
│   │   └── index.md
│   └── learning_paths/
│       └── index.md
├── _outputs/
│   ├── index.md
│   ├── reports/
│   ├── guides/
│   └── slides/
├── _system/
│   ├── index.md
│   ├── manifests/
│   │   └── index.md
│   ├── templates/
│   ├── prompts/
│   ├── lint/
│   └── indexes/
├── _archive/
└── scripts/
```

## Layer model

| Layer       | Purpose                                 |
| ----------- | --------------------------------------- |
| `_raw/`     | Public-safe source notes                |
| `_wiki/`    | Curated public knowledge                |
| `_outputs/` | Public deliverables                     |
| `_system/`  | Schema, templates, manifests, workflows |
| `_archive/` | Retired public material                 |
| `scripts/`  | Helper automation                       |

## Quick navigation

| I want to...             | Start here                         |
| ------------------------ | ---------------------------------- |
| Understand the repo      | `README.md`, `map.md`, `AGENTS.md` |
| Browse knowledge         | `_wiki/index.md`                   |
| Check history            | `_wiki/log.md`                     |
| Understand OKF profile   | `_system/manifests/okf-profile.md` |
| Understand workflow      | `_system/manifests/workflow.md`    |
| Understand privacy rules | `_system/manifests/privacy.md`     |
| Understand Notion sync   | `_system/manifests/notion-sync.md` |
| Add a reference          | `_system/templates/reference.md`   |
| Add a concept            | `_system/templates/concept.md`     |
| Add a claim              | `_system/templates/claim.md`       |
| Add a map                | `_system/templates/map.md`         |
| Add a playbook           | `_system/templates/playbook.md`    |

## Public safety

This repo is public.

Do not add private source paths, private Notion links, private Obsidian links, work-sensitive material, or personal data.

## Rendered site paths

The Quartz site publishes only wiki section folders that contain reviewed public pages beyond `index.md`. Published wiki sections stay under `_wiki/` so the Explorer mirrors the source hierarchy.

Current published section:

- `/_wiki/concepts/`

Unlisted compatibility aliases such as `/concepts/` may exist so old links and Quartz Explorer folder hrefs do not 404. They are not discovery surfaces.

Source-only operating folders such as `_system/` stay in Git and are not copied into the rendered Explorer.
