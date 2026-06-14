---
type: System Manifest
title: Quartz Visual Page Workflow
description: Workflow and lessons for building, publishing, and verifying visual Quartz pages in Knowledge Atlas.
visibility: public
status: active
tags:
  - workflow
  - quartz
  - visual-pages
  - publication
---

# Quartz Visual Page Workflow

Use this workflow when adding or changing public pages that depend on embedded HTML, CSS, diagrams, responsive layout, dark mode, or Quartz rendering behavior.

## Design Direction

Knowledge Atlas should feel warm, neutral, dense, and readable. The dark mode direction is Claude-like: warm charcoal instead of blue-black, cream text instead of stark white, and clay/amber accents instead of saturated neon.

The current global palette lives in `quartz.config.yaml` and the global Quartz polish lives in `quartz/styles/custom.scss`. Embedded page visuals should inherit those tokens rather than inventing a separate theme.

## Why Use HTML Embeds

Use HTML in Markdown when Markdown would make the artifact harder to read or review. The useful pattern is not decoration; it is higher information density, visual clarity, and faster human review.

Good HTML embeds can act as:

- a design-system contact sheet
- a component state matrix
- a compact explainer with diagrams and annotations
- a status or incident report with timelines and small charts
- a lightweight prototype for motion, layout, or interaction decisions

Do not use HTML just to make normal prose look fancy. If a plain Markdown section communicates the idea clearly, keep it Markdown.

## Authoring Rules

- Create public pages as Markdown notes with OKF frontmatter, not standalone `.html` files.
- Put visual pages under the relevant reviewed public section, usually `_wiki/concepts/`.
- Link notable pages from the section `index.md`.
- Use a page-specific class prefix such as `kw-` or `okf-` to avoid CSS collisions.
- Prefer semantic HTML and CSS diagrams over inline SVG unless SVG is clearly needed and verified live.
- Use Quartz theme variables such as `--light`, `--dark`, `--secondary`, `--tertiary`, `--lightgray`, `--gray`, and `--darkgray` instead of hard-coded light surfaces.
- Use local CSS custom properties to alias Quartz variables, for example `--card`, `--muted`, `--accent`, and `--line`.
- Keep all colors warm-neutral by default. Avoid cool gray slabs, neon accents, and generic blue-purple AI palettes.
- Test both light and dark themes. Hard-coded white panels usually fail in Quartz dark mode.
- Tune responsive breakpoints for Quartz's content column, not for a full-width application shell.
- Prefer one strong visual structure over many equal cards. HTML should guide attention, not fill space.

## Embedded HTML Standards

- Start each embed with one wrapper `<section>` and an `aria-label`.
- Put the page-local `<style>` block immediately before the wrapper section.
- Scope every selector under the wrapper prefix.
- Use CSS Grid/Flexbox, not tables, for layout unless the content is truly tabular.
- Keep interaction optional. Public knowledge pages should remain useful with JavaScript disabled.
- If adding controls, sliders, or copy buttons, explain why interaction improves review or understanding.
- Make dense information scannable with labels, timelines, matrices, callouts, and short annotations.
- Use real text in semantic elements rather than baking text into images.
- Avoid huge pasted CSS frameworks, external scripts, remote assets, and hidden data blobs.
- Keep temporary prototypes in private `_outputs/` unless they are reviewed public content.

## Visual Palette Standards

- Dark canvas: `#141413` for depth and `#262624` for the page background.
- Dark surface: `#30302E` for primary panels and `#3A3935` for raised/hovered panels.
- Dark text: `#FAF9F5` primary, `#C2C0B6` secondary, `#9C9A92` tertiary labels.
- Dark accents: `#E08B6B` for clay links/marks, `#A55A3B` for clay fills, and `#D1A041` for amber highlights.
- Dark borders: `rgba(222, 220, 209, 0.15)` soft and `rgba(222, 220, 209, 0.30)` strong.
- Background: warm charcoal in dark mode, warm ivory in light mode.
- Text: cream/off-white on dark mode, dark umber on light mode.
- Borders: low-contrast warm gray, never pure black or pure white.
- Primary accent: clay/rust, used for links, active states, and key marks.
- Secondary accent: muted amber/olive, used sparingly for contrast or diagram categories.
- Surfaces: slightly mixed from `--light`, `--dark`, and accents with `color-mix()`.
- Shadows: soft and low-contrast; do not use glossy card shadows everywhere.
- Normal-size text must meet WCAG AA contrast (`4.5:1`). The clay link `#E08B6B` passes on `#30302E`; the darker clay fill `#A55A3B` is for filled elements with cream text, not small link text on dark surfaces.

## Markdown And HTML Traps

- CommonMark raw HTML blocks are fragile around blank lines and indentation.
- Do not put a blank line before an indented nested `<div>` inside a raw HTML section.
- A blank line followed by indented HTML can be rendered as an escaped code block.
- Keep nested custom HTML contiguous, or left-align raw HTML if a blank line is unavoidable.
- If using inline SVG, verify the live DOM. SVG source can appear as visible text or escaped code if Markdown parsing changes shape.

## Local Checks Before Commit

- Review the rendered source shape in the Markdown file, especially around `<style>`, `<section>`, and nested `<div>` blocks.
- Run `git diff --check`.
- Run a Markdown formatter check when available, for example `npx prettier --check <changed-files>`.
- Check public safety: no private paths, private links, secrets, sensitive details, copied disallowed text, or `visibility: private`.
- Update `_wiki/log.md` for meaningful visual, workflow, or publication changes.

## Public Commit And Deploy Loop

1. Commit the public atlas changes inside this repository first.
2. Push the public atlas commit.
3. Check the GitHub Pages workflow triggered by the pushed commit.
4. Watch the workflow to completion when rendering or deployment behavior changed.
5. Do not update any parent submodule pointer until the public repo has the intended commit.

Useful commands when the GitHub CLI is available:

```sh
gh run list --workflow deploy.yml --limit 1 --json databaseId,status,conclusion,headSha
gh run watch <run-id> --exit-status
```

## Live Browser Verification

Use the live GitHub Pages URL for visual changes, not only source inspection. Add a cache-busting query with the commit hash, for example:

```text
https://falk-eysen.github.io/knowledge-atlas/concepts/example-page?v=<commit>
```

In browser DevTools, verify at least:

- the page loads at the expected route
- the visual root element exists
- dark mode uses Quartz colors
- no custom HTML or SVG appears inside visible `pre` or `code` blocks
- layout is acceptable in the normal desktop Quartz column and on narrow/mobile width

Example DevTools check:

```js
() => {
  document.documentElement.setAttribute("saved-theme", "dark");
  const leakedCodeBlocks = [...document.querySelectorAll("pre, code")]
    .filter((el) =>
      /<div|<svg|<rect|<path|<circle|viewBox/.test(el.textContent),
    )
    .map((el) => el.textContent.slice(0, 160));

  return {
    title: document.title,
    leakedCodeBlocks,
    escapedHtmlInBody: /<div class=|<svg|<rect|<path|<circle|viewBox/.test(
      document.body.innerText,
    ),
    theme: document.documentElement.getAttribute("saved-theme"),
  };
};
```

Take screenshots when visual quality is part of the change. If screenshots are temporary verification artifacts, remove them before committing.

For palette changes, screenshot both the home/index page and at least one visual concept page in dark mode.

## Parent Repository Pointer

If this repository is checked out as a submodule, update the parent repository only after the public atlas commit is pushed. Stage and commit the submodule pointer in the parent separately from the public atlas commit.

Do not stage unrelated untracked files while doing the pointer update.

## Retrospective From The Visual Concept Pages

- Standalone `.html` pages were not the right publication shape; Quartz-routed Markdown notes were safer.
- Inline SVG increased the chance of escaped source leaking into the rendered page.
- HTML/CSS diagrams using Quartz variables worked better for dark mode.
- A blank line before an indented nested `<div>` caused CommonMark to render part of the visual as a code block.
- The first responsive breakpoint was too conservative for the Quartz desktop content column and made cards taller than needed.
- A successful source diff was not enough; the final check needed the deployed site, DevTools DOM inspection, dark mode forcing, and screenshots when useful.

## Source Ideas

- Thariq Shihipar's HTML effectiveness examples: https://thariqs.github.io/html-effectiveness/
- Anthropic article on HTML artifacts with Claude Code: https://claude.com/blog/using-claude-code-the-unreasonable-effectiveness-of-html
- Original X article reference: https://x.com/trq212/article/2052809885763747935
