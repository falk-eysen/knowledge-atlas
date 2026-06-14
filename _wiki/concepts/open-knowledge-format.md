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
    --okf-bg: #f8fbfb;
    --okf-ink: #182324;
    --okf-muted: #5f6f72;
    --okf-line: #d7e4e5;
    --okf-blue: #376f75;
    --okf-gold: #a97828;
    --okf-violet: #6556a3;
    --okf-green: #4d7f56;
    border: 1px solid var(--okf-line);
    border-radius: 28px;
    padding: clamp(1rem, 2.5vw, 2rem);
    background:
      linear-gradient(120deg, rgba(55, 111, 117, 0.12), transparent 30rem),
      radial-gradient(circle at bottom right, rgba(169, 120, 40, 0.14), transparent 28rem),
      var(--okf-bg);
    color: var(--okf-ink);
    box-shadow: 0 24px 70px rgba(24, 35, 36, 0.08);
  }

  .okf-grid {
    display: grid;
    grid-template-columns: minmax(0, 0.8fr) minmax(0, 1.2fr);
    gap: clamp(1rem, 3vw, 2rem);
    align-items: start;
  }

  .okf-kicker {
    color: var(--okf-blue);
    font-size: 0.8rem;
    font-weight: 800;
    letter-spacing: 0.12em;
    text-transform: uppercase;
  }

  .okf-title {
    margin: 0.3rem 0 0.8rem;
    font-size: clamp(2rem, 6vw, 4.4rem);
    line-height: 0.95;
    letter-spacing: -0.06em;
  }

  .okf-lede {
    color: var(--okf-muted);
    font-size: clamp(1rem, 2vw, 1.2rem);
  }

  .okf-note {
    overflow: hidden;
    border: 1px solid var(--okf-line);
    border-radius: 24px;
    background: rgba(255, 255, 255, 0.78);
  }

  .okf-note-header {
    display: flex;
    gap: 0.5rem;
    align-items: center;
    border-bottom: 1px solid var(--okf-line);
    padding: 0.8rem 1rem;
    background: #eef6f6;
  }

  .okf-dot {
    width: 0.75rem;
    height: 0.75rem;
    border-radius: 50%;
    background: var(--color);
  }

  .okf-code {
    display: grid;
    gap: 0.35rem;
    padding: 1rem;
    font-family: "IBM Plex Mono", ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
    font-size: 0.9rem;
  }

  .okf-line {
    display: flex;
    gap: 0.9rem;
  }

  .okf-num {
    min-width: 2ch;
    color: #9aacaf;
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
    gap: 0.9rem;
    margin-top: 1.5rem;
  }

  .okf-tile {
    border: 1px solid var(--okf-line);
    border-top: 0.35rem solid var(--tile);
    border-radius: 18px;
    padding: 1rem;
    background: rgba(255, 255, 255, 0.64);
  }

  .okf-tile b {
    display: block;
    margin-bottom: 0.35rem;
  }

  .okf-tile p {
    margin: 0;
    color: var(--okf-muted);
    font-size: 0.93rem;
  }

  .okf-map {
    margin-top: 1.5rem;
    overflow-x: auto;
  }

  .okf-map svg {
    min-width: 760px;
    width: 100%;
    height: auto;
  }

  @media (max-width: 860px) {
    .okf-grid,
    .okf-schema {
      grid-template-columns: 1fr;
    }
  }
</style>

<section class="okf-visual" aria-label="Visual model of the Open Knowledge Format">
  <div class="okf-grid">
    <div>
      <div class="okf-kicker">Portable knowledge object</div>
      <h2 class="okf-title">Markdown body. YAML identity. Links as structure.</h2>
      <p class="okf-lede">
        OKF keeps knowledge readable as plain text while making it structured enough for navigation, automation, review, and publication.
      </p>
    </div>
    <div class="okf-note" aria-label="Example OKF note structure">
      <div class="okf-note-header" aria-hidden="true">
        <span class="okf-dot" style="--color: #d96c5f"></span>
        <span class="okf-dot" style="--color: #e8b84e"></span>
        <span class="okf-dot" style="--color: #62a76f"></span>
      </div>
      <div class="okf-code">
        <div class="okf-line"><span class="okf-num">1</span><span class="okf-yaml">---</span></div>
        <div class="okf-line"><span class="okf-num">2</span><span class="okf-yaml">type: Concept</span></div>
        <div class="okf-line"><span class="okf-num">3</span><span class="okf-yaml">title: Knowledge Object</span></div>
        <div class="okf-line"><span class="okf-num">4</span><span class="okf-yaml">visibility: public</span></div>
        <div class="okf-line"><span class="okf-num">5</span><span class="okf-yaml">status: active</span></div>
        <div class="okf-line"><span class="okf-num">6</span><span class="okf-yaml">tags: [okf, concept]</span></div>
        <div class="okf-line"><span class="okf-num">7</span><span class="okf-yaml">relations:</span></div>
        <div class="okf-line"><span class="okf-num">8</span><span class="okf-yaml">  derived_from: [source]</span></div>
        <div class="okf-line"><span class="okf-num">9</span><span class="okf-yaml">---</span></div>
        <div class="okf-line"><span class="okf-num">10</span><span class="okf-md"># Knowledge Object</span></div>
        <div class="okf-line"><span class="okf-num">11</span><span class="okf-md">A claim, concept, map, or output with</span></div>
        <div class="okf-line"><span class="okf-num">12</span><span class="okf-link">links to evidence and related pages.</span></div>
      </div>
    </div>
  </div>

  <div class="okf-schema">
    <div class="okf-tile" style="--tile: var(--okf-violet)">
      <b>Identity</b>
      <p>Type, title, description, status, visibility, and tags.</p>
    </div>
    <div class="okf-tile" style="--tile: var(--okf-blue)">
      <b>Body</b>
      <p>Plain Markdown that stays readable without a database.</p>
    </div>
    <div class="okf-tile" style="--tile: var(--okf-gold)">
      <b>Relations</b>
      <p>Links and frontmatter edges connect pages into a graph.</p>
    </div>
    <div class="okf-tile" style="--tile: var(--okf-green)">
      <b>Provenance</b>
      <p>Sources and derived-from fields keep knowledge grounded.</p>
    </div>
  </div>

  <div class="okf-map" role="img" aria-label="Open Knowledge Format flow from source to knowledge object to graph and outputs">
    <svg viewBox="0 0 1120 360" xmlns="http://www.w3.org/2000/svg">
      <defs>
        <marker id="okf-arrow" markerWidth="12" markerHeight="12" refX="10" refY="6" orient="auto">
          <path d="M2 2 L10 6 L2 10 Z" fill="#5f6f72" />
        </marker>
        <filter id="okf-shadow" x="-20%" y="-20%" width="140%" height="140%">
          <feDropShadow dx="0" dy="12" stdDeviation="12" flood-color="#182324" flood-opacity="0.12" />
        </filter>
      </defs>

      <rect x="40" y="92" width="190" height="112" rx="26" fill="#ffffff" stroke="#d7e4e5" filter="url(#okf-shadow)" />
      <text x="135" y="137" text-anchor="middle" font-size="18" font-weight="800" fill="#182324">Source</text>
      <text x="135" y="166" text-anchor="middle" font-size="14" fill="#5f6f72">book, web, paper</text>

      <path d="M235 148 H330" stroke="#5f6f72" stroke-width="3" marker-end="url(#okf-arrow)" />

      <rect x="335" y="58" width="250" height="180" rx="30" fill="#ffffff" stroke="#d7e4e5" filter="url(#okf-shadow)" />
      <text x="460" y="98" text-anchor="middle" font-size="18" font-weight="800" fill="#376f75">OKF page</text>
      <rect x="370" y="120" width="180" height="26" rx="8" fill="#f1eefb" />
      <text x="460" y="139" text-anchor="middle" font-size="13" fill="#6556a3">YAML frontmatter</text>
      <rect x="370" y="154" width="180" height="26" rx="8" fill="#edf7f7" />
      <text x="460" y="173" text-anchor="middle" font-size="13" fill="#376f75">Markdown body</text>
      <rect x="370" y="188" width="180" height="26" rx="8" fill="#fff5df" />
      <text x="460" y="207" text-anchor="middle" font-size="13" fill="#a97828">Relations and sources</text>

      <path d="M590 148 H690" stroke="#5f6f72" stroke-width="3" marker-end="url(#okf-arrow)" />

      <circle cx="790" cy="148" r="74" fill="#eef8f8" stroke="#8bb6bd" filter="url(#okf-shadow)" />
      <circle cx="760" cy="126" r="15" fill="#376f75" />
      <circle cx="822" cy="124" r="15" fill="#a97828" />
      <circle cx="790" cy="176" r="15" fill="#6556a3" />
      <path d="M774 132 L808 126 M768 138 L784 164 M814 138 L797 164" stroke="#5f6f72" stroke-width="3" />
      <text x="790" y="252" text-anchor="middle" font-size="18" font-weight="800" fill="#182324">Knowledge graph</text>

      <path d="M866 148 H960" stroke="#5f6f72" stroke-width="3" marker-end="url(#okf-arrow)" />

      <rect x="965" y="92" width="120" height="112" rx="26" fill="#fff8e9" stroke="#dfc47c" filter="url(#okf-shadow)" />
      <text x="1025" y="137" text-anchor="middle" font-size="18" font-weight="800" fill="#a97828">Output</text>
      <text x="1025" y="166" text-anchor="middle" font-size="14" fill="#5f6f72">site, report, API</text>

      <path d="M460 244 V304 H790 V230" stroke="#6556a3" stroke-width="3" stroke-dasharray="8 8" marker-end="url(#okf-arrow)" />
      <text x="606" y="324" text-anchor="middle" font-size="13" fill="#6556a3">frontmatter keeps automation explicit</text>
    </svg>

  </div>
</section>

## Why this matters

OKF keeps the atlas simple enough for Git, Markdown editors, and static site generators, while preserving enough structure for review, navigation, search, sync, and LLM-assisted synthesis.
