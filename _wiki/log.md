# Public wiki log

Newest entries first.

## 2026-06-14

- **Design**: Applied an Impeccable-informed polish pass to public visual embeds: stronger page-specific motifs, higher OKF code contrast, compact ObjectGraph mobile metrics, cleaner mobile tag wrapping, and wider desktop diagram canvas.
- **Design**: Fixed mobile clipping in public visual embeds after Playwright checks across `320`, `360`, `390`, `430`, `520`, and `640` px widths.
- **Concepts**: Added a public ObjectGraph visual concept page synthesizing the arXiv paper into an agent-native document traversal model.
- **Site navigation**: Changed rendered wiki paths to `/wiki/`, stopped publishing `log.md`, `README.md`, and `map.md` into GitHub Pages, and removed compatibility aliases because Quartz still exposed them in Explorer.
- **Site navigation**: Kept source-only system docs, empty taxonomy folders, and empty `_outputs` out of the rendered Quartz Explorer.
- **Design**: Moved visual concept page CSS out of Markdown and into scoped site SCSS after Playwright search testing showed inline style blocks polluted search excerpts.
- **Design**: Tightened mobile explorer width containment while verifying the matte dark palette on deployed pages.
- **Design**: Finalized the matte warm dark palette around Claude/Radix Sand-inspired tokens: charcoal canvas, cream text, clay links, amber highlights, and low-contrast warm borders.
- **Design**: Shifted the Quartz site toward a warm neutral Claude-like palette, added a site-wide `custom.scss` override, and expanded HTML-in-Markdown standards for dense visual artifacts.
- **Workflow**: Added a Quartz visual page workflow with authoring rules, Markdown/HTML rendering traps, deploy verification, DevTools checks, and lessons from the visual concept pages.
- **Agent workflow**: Modernized `AGENTS.md` into a concise public-safe entrypoint with linked manifests, validation expectations, and Quartz deployment guidance.
- **Concepts**: Restyled the visual concept pages for Quartz dark mode and replaced inline SVG diagrams with HTML/CSS diagrams.
- **Concepts**: Added visual concept pages for the Karpathy-style LLM wiki architecture and OKF.
- **Site navigation**: Added folder notes for public atlas sections and flattened wiki section paths for Quartz URLs such as `/concepts/`.
- **Site**: Added Quartz/GitHub Pages configuration for rendering the public atlas from selected public-safe sections.
- **Initialization**: Established `knowledge-atlas` as a public curated knowledge atlas.
- **Format**: Adopted an OKF-compatible Markdown/YAML profile.
- **Workflow**: Defined public publication as reviewed output from private synthesis, never automatic private sync.
- **Notion role**: Defined Notion as a workflow and reference surface, not the canonical source of public content.
- **Safety**: Established that the public repo must never link back to private notes.
