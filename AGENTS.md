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

This is the agent entrypoint for `knowledge-atlas`, a public OKF-compatible knowledge catalog rendered with Quartz on GitHub Pages.

Everything in this repository must be safe for public readers.

## Start Here

Read in this order when relevant:

1. [`map.md`](map.md) - high-level repository layout and published site paths
2. [`index.md`](index.md) - OKF bundle entrypoint
3. [`CONTRIBUTING.md`](CONTRIBUTING.md) - public contribution expectations
4. [`_wiki/index.md`](_wiki/index.md) - public knowledge index
5. [`_wiki/log.md`](_wiki/log.md) - chronological update log
6. [`_system/manifests/okf-profile.md`](_system/manifests/okf-profile.md) - Markdown/frontmatter rules
7. [`_system/manifests/workflow.md`](_system/manifests/workflow.md) - publication workflow and site build shape
8. [`_system/manifests/quartz-visual-pages.md`](_system/manifests/quartz-visual-pages.md) - visual page authoring and verification workflow
9. [`_system/manifests/privacy.md`](_system/manifests/privacy.md) - public safety rules
10. [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml) - Quartz/GitHub Pages deployment

## Repository Map

- `_raw/` - public-safe source notes and references
- `_wiki/` - curated public knowledge: concepts, references, claims, maps, playbooks, patterns, learning paths, projects, areas, themes, and open questions
- `_outputs/` - public deliverables
- `_system/` - schemas, manifests, templates, prompts, lint reports, indexes, and workflow material
- `_archive/` - retired public material
- `scripts/` - helper automation, when present

## Working Rules

- Inspect nearby pages, templates, and indexes before adding new content.
- Put public source notes in `_raw/`.
- Put synthesized public knowledge in `_wiki/`.
- Put public deliverables in `_outputs/`.
- Put repository operating material in `_system/`.
- Use normal Markdown links.
- Include OKF-compatible YAML frontmatter on normal Markdown files; `index.md` and `log.md` are reserved navigation/history files.
- Cite public sources for factual claims when possible.
- Keep uncertainty visible; do not overstate claims.
- Published wiki section folders should have an `index.md` folder note. Empty taxonomy folders stay source-only until they contain reviewed public pages.

## Public Boundary

Do not commit:

- credentials, tokens, keys, passwords, or secret values
- private local filesystem paths
- private repo or vault names
- private Notion or Obsidian links
- workplace-sensitive details
- customer identifiers
- unnecessary personal data
- copied copyrighted text that is not clearly allowed
- files with `visibility: private`

Reviewed material may come from private workspaces, but private identifiers and private source paths stay out of this repository.

## Validation

There is no package manifest in this repo. Do not invent local build commands.

Before finishing a content change, use the narrowest checks that apply:

- Confirm changed normal Markdown files have public OKF-compatible frontmatter.
- Check public safety: no private paths, private links, secrets, sensitive details, or `visibility: private`.
- Check links and citations you added or changed.
- Update section `index.md` files when adding notable pages.
- Append `_wiki/log.md` for meaningful public content, workflow, publication, or instruction changes.

Before finishing a site or deployment change:

- Review `.github/workflows/deploy.yml` for the actual Quartz build path.
- Confirm only populated public sections are copied into Quartz content.
- Confirm excluded areas remain excluded from the site build: `_raw/`, `_archive/`, `scripts/`, local editor state, and private/draft filename patterns.
- Follow `_system/manifests/quartz-visual-pages.md` for embedded HTML/CSS, visual diagrams, dark-mode, or responsive rendering changes.
- Verify GitHub Pages after push when the change affects rendering or deployment.

## Required Updates

- Update `map.md` when top-level structure or published site paths change.
- Update `_wiki/index.md` when major public wiki pages or clusters are added.
- Append `_wiki/log.md` when public content, workflow, publication, or instruction rules change.
- Update `_system/manifests/...` when OKF schema, workflow, privacy, or publication behavior changes.

## Maintenance

Keep this file short. Update it only when agent entrypoints, validation expectations, safety rules, repository structure, or deployment shape changes.

Do not add `CLAUDE.md`, Copilot instructions, Cursor rules, Gemini files, or other harness adapters unless the repo actually starts using those tools.
