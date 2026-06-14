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
