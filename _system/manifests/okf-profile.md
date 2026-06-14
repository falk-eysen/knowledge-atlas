---
type: System Manifest
title: Public OKF Profile
description: OKF-compatible profile used by Knowledge Atlas.
visibility: public
status: active
tags:
  - okf
  - schema
  - markdown
---

# Public OKF Profile

Knowledge Atlas uses an OKF-compatible Markdown profile.

OKF is based on:

```text
Markdown files
YAML frontmatter
directory hierarchy
normal Markdown links
reserved index/log files
```

## Reserved files

```text
index.md
log.md
```

`index.md` files provide navigation.

`log.md` files provide chronological update history.

## Normal Markdown files

Every normal Markdown file should contain YAML frontmatter with a non-empty `type`.

Baseline:

```yaml
---
type: Concept
title: Example
description: One sentence summary.
visibility: public
status: draft
tags:
  - example
created: 2026-06-14
updated: 2026-06-14
---
```

## Required local fields

```yaml
type:
title:
description:
visibility:
status:
tags:
```

## Recommended local fields

```yaml
id:
created:
updated:
resource:
sources:
relations:
curation:
sync:
```

## Visibility

Public repo files should use:

```yaml
visibility: public
```

Do not commit files with:

```yaml
visibility: private
```

## Status values

```yaml
status: draft
status: active
status: curated
status: archived
```

## Curation values

```yaml
curation: seed
curation: useful
curation: recommended
curation: canonical
curation: disputed
curation: outdated
```

## Common types

```yaml
type: Concept
type: Reference
type: Claim
type: Map
type: Playbook
type: Pattern
type: Learning Path
type: Project
type: Open Question
type: System Document
type: System Manifest
type: Template
```

## Link style

Prefer standard Markdown links.

Good:

```md
[Context Engineering](/_wiki/concepts/context-engineering.md)
```

Avoid private-only Obsidian references in public pages.

## Citations

If a page makes factual claims based on external material, include a `# Citations` section.

Example:

```md
# Citations

[1] [Original source](https://example.com)
```

## Consumer tolerance

Consumers should tolerate:

- unknown `type` values
- unknown frontmatter keys
- missing optional fields
- broken links
- missing indexes

The goal is durable interoperability, not brittle perfection.
