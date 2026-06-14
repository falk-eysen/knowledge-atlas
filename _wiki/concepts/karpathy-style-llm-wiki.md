---
type: Concept
title: Karpathy-Style LLM Wiki
description: A visual model of an LLM-oriented wiki that separates raw sources, synthesized knowledge, generated outputs, and operating system files.
visibility: public
status: active
tags:
  - concepts
  - llm-wiki
  - knowledge-architecture
---

# Karpathy-Style LLM Wiki

This visual explains the repository shape used by the atlas: capture evidence first, synthesize durable knowledge second, and publish outputs only after review.

<style>
  .kw-visual {
    --kw-border: var(--lightgray);
    --kw-text: var(--dark);
    --kw-muted: var(--darkgray);
    --kw-card: var(--light);
    --kw-raw: #c77756;
    --kw-wiki: var(--secondary);
    --kw-output: var(--tertiary);
    --kw-system: #9b8cff;
    border: 1px solid var(--kw-border);
    border-radius: 1.35rem;
    padding: clamp(1rem, 2.5vw, 1.6rem);
    background: var(--light);
    background: linear-gradient(135deg, color-mix(in srgb, var(--light) 92%, var(--secondary) 8%), color-mix(in srgb, var(--light) 94%, var(--tertiary) 6%));
    color: var(--kw-text);
  }

  .kw-visual * {
    box-sizing: border-box;
  }

  .kw-intro {
    display: grid;
    grid-template-columns: minmax(0, 0.95fr) minmax(16rem, 1.05fr);
    gap: clamp(1rem, 3vw, 1.5rem);
    align-items: start;
  }

  .kw-kicker {
    color: var(--kw-wiki);
    font-size: 0.78rem;
    font-weight: 800;
    letter-spacing: 0.12em;
    text-transform: uppercase;
  }

  .kw-title {
    margin: 0.35rem 0 0.8rem;
    max-width: 11ch;
    font-size: clamp(2.1rem, 5vw, 3.8rem);
    line-height: 0.98;
    letter-spacing: -0.055em;
  }

  .kw-lede {
    max-width: 34rem;
    margin: 0;
    color: var(--kw-muted);
    font-size: 1.02rem;
  }

  .kw-layers,
  .kw-principles {
    display: grid;
    gap: 0.75rem;
  }

  .kw-layer,
  .kw-principle,
  .kw-step {
    border: 1px solid var(--kw-border);
    border-radius: 1rem;
    background: var(--kw-card);
    background: color-mix(in srgb, var(--light) 88%, var(--dark) 12%);
  }

  .kw-layer {
    display: grid;
    grid-template-columns: 0.45rem minmax(0, 1fr);
    min-height: 4.35rem;
    overflow: hidden;
  }

  .kw-band {
    background: var(--layer-color);
  }

  .kw-layer-body {
    padding: 0.85rem 1rem;
  }

  .kw-layer strong,
  .kw-step strong,
  .kw-principle strong {
    display: block;
    color: var(--kw-text);
  }

  .kw-layer span,
  .kw-step span,
  .kw-principle span {
    display: block;
    margin-top: 0.25rem;
    color: var(--kw-muted);
    font-size: 0.92rem;
    line-height: 1.45;
  }

  .kw-routes {
    display: grid;
    gap: 1rem;
    margin-top: 1.25rem;
  }

  .kw-route-title {
    margin-bottom: 0.45rem;
    color: var(--kw-muted);
    font-size: 0.78rem;
    font-weight: 800;
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  .kw-rail {
    display: grid;
    grid-template-columns: minmax(0, 1fr) auto minmax(0, 1fr) auto minmax(0, 1fr) auto minmax(0, 1fr);
    gap: 0.55rem;
    align-items: stretch;
  }

  .kw-rail-short {
    grid-template-columns: minmax(0, 1fr) auto minmax(0, 1fr) auto minmax(0, 1fr);
  }

  .kw-step {
    min-height: 6.25rem;
    padding: 0.9rem;
  }

  .kw-step small {
    display: inline-block;
    margin-bottom: 0.55rem;
    color: var(--step-color);
    font-size: 0.72rem;
    font-weight: 900;
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }

  .kw-arrow {
    align-self: center;
    color: var(--kw-muted);
    font-weight: 900;
  }

  .kw-principles {
    grid-template-columns: repeat(3, minmax(0, 1fr));
    margin-top: 1.25rem;
  }

  .kw-principle {
    padding: 0.95rem;
  }

  @media (max-width: 900px) {
    .kw-intro,
    .kw-principles {
      grid-template-columns: 1fr;
    }

    .kw-rail,
    .kw-rail-short {
      grid-template-columns: repeat(2, minmax(0, 1fr));
    }

    .kw-arrow {
      display: none;
    }
  }

  @media (max-width: 520px) {
    .kw-rail,
    .kw-rail-short {
      grid-template-columns: 1fr;
    }
  }
</style>

<section class="kw-visual" aria-label="Visual model of a Karpathy-style LLM wiki">
  <div class="kw-intro">
    <div>
      <div class="kw-kicker">LLM wiki architecture</div>
      <h2 class="kw-title">Evidence becomes memory.</h2>
      <p class="kw-lede">
        A Karpathy-style wiki treats a repository as working memory for humans and language models. It keeps evidence, durable synthesis, generated deliverables, and operating rules in separate layers.
      </p>
    </div>
    <div class="kw-layers" aria-label="Repository layers">
      <div class="kw-layer" style="--layer-color: var(--kw-raw)">
        <div class="kw-band"></div>
        <div class="kw-layer-body">
          <strong>_raw/</strong>
          <span>Evidence, captures, excerpts, source notes, and scratch thinking.</span>
        </div>
      </div>
      <div class="kw-layer" style="--layer-color: var(--kw-wiki)">
        <div class="kw-band"></div>
        <div class="kw-layer-body">
          <strong>_wiki/</strong>
          <span>Compiled concepts, claims, maps, questions, patterns, and project knowledge.</span>
        </div>
      </div>
      <div class="kw-layer" style="--layer-color: var(--kw-output)">
        <div class="kw-band"></div>
        <div class="kw-layer-body">
          <strong>_outputs/</strong>
          <span>Reports, guides, summaries, decks, and reusable public deliverables.</span>
        </div>
      </div>
      <div class="kw-layer" style="--layer-color: var(--kw-system)">
        <div class="kw-band"></div>
        <div class="kw-layer-body">
          <strong>_system/</strong>
          <span>Schemas, prompts, templates, manifests, lint rules, and workflow controls.</span>
        </div>
      </div>
    </div>
  </div>

  <div class="kw-routes">
    <div>
      <div class="kw-route-title">Learning loop</div>
      <div class="kw-rail" role="list" aria-label="Learning loop from capture to wiki">
        <div class="kw-step" style="--step-color: var(--kw-raw)" role="listitem">
          <small>1 Capture</small>
          <strong>Collect traces</strong>
          <span>Clips, notes, links, papers, repos, and observations.</span>
        </div>
        <div class="kw-arrow" aria-hidden="true">→</div>
        <div class="kw-step" style="--step-color: var(--kw-raw)" role="listitem">
          <small>2 Raw</small>
          <strong>Preserve source context</strong>
          <span>Keep source material grounded before interpreting it.</span>
        </div>
        <div class="kw-arrow" aria-hidden="true">→</div>
        <div class="kw-step" style="--step-color: var(--kw-wiki)" role="listitem">
          <small>3 Synthesis</small>
          <strong>Distill and connect</strong>
          <span>Turn material into concepts, claims, maps, and questions.</span>
        </div>
        <div class="kw-arrow" aria-hidden="true">→</div>
        <div class="kw-step" style="--step-color: var(--kw-wiki)" role="listitem">
          <small>4 Wiki</small>
          <strong>Store durable knowledge</strong>
          <span>Make reusable memory available to future work.</span>
        </div>
      </div>
    </div>

    <div>
      <div class="kw-route-title">Publication loop</div>
      <div class="kw-rail kw-rail-short" role="list" aria-label="Publication loop from wiki to public atlas">
        <div class="kw-step" style="--step-color: var(--kw-output)" role="listitem">
          <small>5 Output</small>
          <strong>Create artifacts</strong>
          <span>Reports, guides, summaries, and public pages.</span>
        </div>
        <div class="kw-arrow" aria-hidden="true">→</div>
        <div class="kw-step" style="--step-color: var(--kw-system)" role="listitem">
          <small>6 Review</small>
          <strong>Check safety and quality</strong>
          <span>Privacy, provenance, links, status, and usefulness.</span>
        </div>
        <div class="kw-arrow" aria-hidden="true">→</div>
        <div class="kw-step" style="--step-color: var(--kw-wiki)" role="listitem">
          <small>7 Publish</small>
          <strong>Expose only curated pages</strong>
          <span>The public atlas is a reviewed layer, not a mirror.</span>
        </div>
      </div>
    </div>

  </div>

  <div class="kw-principles">
    <div class="kw-principle">
      <strong>Separate evidence from synthesis</strong>
      <span>Raw material stays traceable; wiki pages state what was learned.</span>
    </div>
    <div class="kw-principle">
      <strong>Make the graph navigable</strong>
      <span>Concepts, claims, maps, and questions link across the knowledge base.</span>
    </div>
    <div class="kw-principle">
      <strong>Publish only after review</strong>
      <span>Public pages are curated outputs, not automatic mirrors of private notes.</span>
    </div>
  </div>
</section>

## Why this matters

The structure lets an LLM reuse context without flattening everything into one prompt. Raw material remains available for grounding, wiki pages provide durable memory, and system files keep the workflow legible.
