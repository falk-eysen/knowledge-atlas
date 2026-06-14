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

## Authoring Rules

- Create public pages as Markdown notes with OKF frontmatter, not standalone `.html` files.
- Put visual pages under the relevant reviewed public section, usually `_wiki/concepts/`.
- Link notable pages from the section `index.md`.
- Use a page-specific class prefix such as `kw-` or `okf-` to avoid CSS collisions.
- Prefer HTML/CSS diagrams over inline SVG unless SVG is clearly needed and verified live.
- Use Quartz theme variables such as `--light`, `--dark`, `--secondary`, `--tertiary`, `--lightgray`, and `--darkgray` instead of hard-coded light surfaces.
- Test both light and dark themes. Hard-coded white panels usually fail in Quartz dark mode.
- Tune responsive breakpoints for Quartz's content column, not for a full-width application shell.

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
