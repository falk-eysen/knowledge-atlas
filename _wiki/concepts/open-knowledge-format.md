---
type: Concept
title: Open Knowledge Format
description: A visual model of OKF as a lightweight Markdown/YAML structure for portable, linked, provenance-aware knowledge.
visibility: public
status: active
tags:
  - concepts
  - okf
  - knowledge-architecture
---

# Open Knowledge Format

OKF is the public atlas convention for turning Markdown notes into portable knowledge objects with metadata, links, and provenance.

<style>
  .okf-visual {
    --okf-border: var(--lightgray);
    --okf-text: var(--dark);
    --okf-muted: var(--darkgray);
    --okf-card: var(--light);
    --okf-blue: var(--secondary);
    --okf-gold: var(--tertiary);
    --okf-violet: #9b8cff;
    --okf-green: #6cbf7d;
    border: 1px solid var(--okf-border);
    border-radius: 1.35rem;
    padding: clamp(1rem, 2.5vw, 1.6rem);
    background: var(--light);
    background: linear-gradient(135deg, color-mix(in srgb, var(--light) 92%, var(--secondary) 8%), color-mix(in srgb, var(--light) 94%, var(--tertiary) 6%));
    color: var(--okf-text);
  }

  .okf-visual * {
    box-sizing: border-box;
  }

  .okf-intro {
    display: grid;
    grid-template-columns: minmax(0, 0.85fr) minmax(17rem, 1.15fr);
    gap: clamp(1rem, 3vw, 1.5rem);
    align-items: start;
  }

  .okf-kicker {
    color: var(--okf-blue);
    font-size: 0.78rem;
    font-weight: 800;
    letter-spacing: 0.12em;
    text-transform: uppercase;
  }

  .okf-title {
    margin: 0.35rem 0 0.8rem;
    max-width: 12ch;
    font-size: clamp(2rem, 5vw, 3.65rem);
    line-height: 0.98;
    letter-spacing: -0.055em;
  }

  .okf-lede {
    max-width: 32rem;
    margin: 0;
    color: var(--okf-muted);
    font-size: 1.02rem;
  }

  .okf-note,
  .okf-tile,
  .okf-node {
    border: 1px solid var(--okf-border);
    border-radius: 1rem;
    background: var(--okf-card);
    background: color-mix(in srgb, var(--light) 88%, var(--dark) 12%);
  }

  .okf-note {
    overflow: hidden;
  }

  .okf-note-bar {
    display: flex;
    gap: 0.45rem;
    align-items: center;
    border-bottom: 1px solid var(--okf-border);
    padding: 0.72rem 0.9rem;
    background: color-mix(in srgb, var(--light) 82%, var(--secondary) 18%);
  }

  .okf-dot {
    width: 0.72rem;
    height: 0.72rem;
    border-radius: 999px;
    background: var(--dot);
  }

  .okf-code {
    display: grid;
    gap: 0.28rem;
    padding: 0.95rem;
    overflow-x: auto;
    font-family: "IBM Plex Mono", ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
    font-size: 0.86rem;
    line-height: 1.45;
  }

  .okf-code-row {
    display: grid;
    grid-template-columns: 2ch minmax(18rem, 1fr);
    gap: 0.9rem;
  }

  .okf-num {
    color: color-mix(in srgb, var(--okf-muted) 70%, transparent);
    user-select: none;
  }

  .okf-yaml {
    color: var(--okf-violet);
  }

  .okf-md {
    color: var(--okf-blue);
  }

  .okf-link {
    color: var(--okf-gold);
  }

  .okf-schema {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));
    gap: 0.75rem;
    margin-top: 1.25rem;
  }

  .okf-tile {
    border-top: 0.3rem solid var(--tile);
    padding: 0.9rem;
  }

  .okf-tile strong,
  .okf-node strong {
    display: block;
    color: var(--okf-text);
  }

  .okf-tile span,
  .okf-node span {
    display: block;
    margin-top: 0.25rem;
    color: var(--okf-muted);
    font-size: 0.92rem;
    line-height: 1.45;
  }

  .okf-flow {
    margin-top: 1.25rem;
  }

  .okf-flow-title {
    margin-bottom: 0.45rem;
    color: var(--okf-muted);
    font-size: 0.78rem;
    font-weight: 800;
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  .okf-rail {
    display: grid;
    grid-template-columns: minmax(0, 1fr) auto minmax(0, 1fr) auto minmax(0, 1fr) auto minmax(0, 1fr);
    gap: 0.55rem;
    align-items: stretch;
  }

  .okf-node {
    min-height: 6.4rem;
    padding: 0.9rem;
  }

  .okf-node small {
    display: inline-block;
    margin-bottom: 0.55rem;
    color: var(--node-color);
    font-size: 0.72rem;
    font-weight: 900;
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }

  .okf-arrow {
    align-self: center;
    color: var(--okf-muted);
    font-weight: 900;
  }

  @media (max-width: 900px) {
    .okf-intro,
    .okf-schema {
      grid-template-columns: 1fr;
    }

    .okf-rail {
      grid-template-columns: 1fr;
    }

    .okf-arrow {
      justify-self: center;
      transform: rotate(90deg);
    }
  }
</style>

<section class="okf-visual" aria-label="Visual model of the Open Knowledge Format">
  <div class="okf-intro">
    <div>
      <div class="okf-kicker">Portable knowledge object</div>
      <h2 class="okf-title">Plain text with structure.</h2>
      <p class="okf-lede">
        OKF keeps knowledge readable as Markdown while making it structured enough for navigation, automation, review, publication, and LLM-assisted synthesis.
      </p>
    </div>
    <div class="okf-note" aria-label="Example OKF note structure">
      <div class="okf-note-bar" aria-hidden="true">
        <span class="okf-dot" style="--dot: #d96c5f"></span>
        <span class="okf-dot" style="--dot: #e8b84e"></span>
        <span class="okf-dot" style="--dot: #62a76f"></span>
      </div>
      <div class="okf-code">
        <div class="okf-code-row"><span class="okf-num">1</span><span class="okf-yaml">---</span></div>
        <div class="okf-code-row"><span class="okf-num">2</span><span class="okf-yaml">type: Concept</span></div>
        <div class="okf-code-row"><span class="okf-num">3</span><span class="okf-yaml">title: Knowledge Object</span></div>
        <div class="okf-code-row"><span class="okf-num">4</span><span class="okf-yaml">visibility: public</span></div>
        <div class="okf-code-row"><span class="okf-num">5</span><span class="okf-yaml">status: active</span></div>
        <div class="okf-code-row"><span class="okf-num">6</span><span class="okf-yaml">tags: [okf, concept]</span></div>
        <div class="okf-code-row"><span class="okf-num">7</span><span class="okf-yaml">relations:</span></div>
        <div class="okf-code-row"><span class="okf-num">8</span><span class="okf-yaml">  derived_from: [source]</span></div>
        <div class="okf-code-row"><span class="okf-num">9</span><span class="okf-yaml">---</span></div>
        <div class="okf-code-row"><span class="okf-num">10</span><span class="okf-md"># Knowledge Object</span></div>
        <div class="okf-code-row"><span class="okf-num">11</span><span class="okf-md">A claim, concept, map, or output with</span></div>
        <div class="okf-code-row"><span class="okf-num">12</span><span class="okf-link">links to evidence and related pages.</span></div>
      </div>
    </div>
  </div>

  <div class="okf-schema" aria-label="OKF page components">
    <div class="okf-tile" style="--tile: var(--okf-violet)">
      <strong>Identity</strong>
      <span>Type, title, description, status, visibility, and tags.</span>
    </div>
    <div class="okf-tile" style="--tile: var(--okf-blue)">
      <strong>Body</strong>
      <span>Plain Markdown that stays readable without a database.</span>
    </div>
    <div class="okf-tile" style="--tile: var(--okf-gold)">
      <strong>Relations</strong>
      <span>Links and frontmatter edges connect pages into a graph.</span>
    </div>
    <div class="okf-tile" style="--tile: var(--okf-green)">
      <strong>Provenance</strong>
      <span>Sources and derived-from fields keep knowledge grounded.</span>
    </div>
  </div>

  <div class="okf-flow">
    <div class="okf-flow-title">Knowledge object lifecycle</div>
    <div class="okf-rail" role="list" aria-label="Open Knowledge Format lifecycle from source to output">
      <div class="okf-node" style="--node-color: var(--okf-gold)" role="listitem">
        <small>Source</small>
        <strong>Evidence enters</strong>
        <span>Books, web pages, papers, repos, or public source notes.</span>
      </div>
      <div class="okf-arrow" aria-hidden="true">→</div>
      <div class="okf-node" style="--node-color: var(--okf-violet)" role="listitem">
        <small>OKF page</small>
        <strong>Metadata wraps Markdown</strong>
        <span>Frontmatter makes identity, status, and relations explicit.</span>
      </div>
      <div class="okf-arrow" aria-hidden="true">→</div>
      <div class="okf-node" style="--node-color: var(--okf-blue)" role="listitem">
        <small>Graph</small>
        <strong>Links create structure</strong>
        <span>Pages become browseable, searchable, and reusable.</span>
      </div>
      <div class="okf-arrow" aria-hidden="true">→</div>
      <div class="okf-node" style="--node-color: var(--okf-green)" role="listitem">
        <small>Output</small>
        <strong>Rendered or reused</strong>
        <span>The same note can feed a site, report, sync, or API.</span>
      </div>
    </div>
  </div>
</section>

## Why this matters

OKF keeps the atlas simple enough for Git, Markdown editors, and static site generators, while preserving enough structure for review, navigation, search, sync, and LLM-assisted synthesis.
