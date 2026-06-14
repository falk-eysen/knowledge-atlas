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
    --kw-bg: #fbfaf7;
    --kw-ink: #241f1a;
    --kw-muted: #6f675c;
    --kw-line: #ded6ca;
    --kw-raw: #8a5a44;
    --kw-wiki: #376f75;
    --kw-out: #8b6f2f;
    --kw-system: #5e548e;
    border: 1px solid var(--kw-line);
    border-radius: 28px;
    padding: clamp(1rem, 2.5vw, 2rem);
    background:
      radial-gradient(circle at top left, rgba(139, 111, 47, 0.16), transparent 34rem),
      linear-gradient(135deg, #fffdf8, var(--kw-bg));
    color: var(--kw-ink);
    box-shadow: 0 24px 70px rgba(36, 31, 26, 0.08);
  }

  .kw-hero {
    display: grid;
    grid-template-columns: minmax(0, 1.1fr) minmax(18rem, 0.9fr);
    gap: clamp(1rem, 3vw, 2rem);
    align-items: center;
  }

  .kw-kicker {
    color: var(--kw-wiki);
    font-size: 0.8rem;
    font-weight: 800;
    letter-spacing: 0.12em;
    text-transform: uppercase;
  }

  .kw-title {
    margin: 0.3rem 0 0.8rem;
    font-size: clamp(2rem, 6vw, 4.6rem);
    line-height: 0.95;
    letter-spacing: -0.07em;
  }

  .kw-lede {
    max-width: 50rem;
    color: var(--kw-muted);
    font-size: clamp(1rem, 2vw, 1.2rem);
  }

  .kw-stack {
    display: grid;
    gap: 0.8rem;
  }

  .kw-card {
    position: relative;
    border: 1px solid var(--kw-line);
    border-left: 0.5rem solid var(--accent);
    border-radius: 20px;
    padding: 1rem;
    background: rgba(255, 255, 255, 0.76);
  }

  .kw-card strong {
    display: block;
    margin-bottom: 0.2rem;
    font-size: 1.08rem;
  }

  .kw-card span {
    color: var(--kw-muted);
    font-size: 0.94rem;
  }

  .kw-flow {
    margin-top: clamp(1.2rem, 4vw, 2.6rem);
    overflow-x: auto;
  }

  .kw-flow svg {
    min-width: 760px;
    width: 100%;
    height: auto;
  }

  .kw-principles {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 0.9rem;
    margin-top: 1.3rem;
  }

  .kw-principle {
    border: 1px solid var(--kw-line);
    border-radius: 18px;
    padding: 1rem;
    background: rgba(255, 255, 255, 0.55);
  }

  .kw-principle b {
    display: block;
    margin-bottom: 0.35rem;
  }

  .kw-principle p {
    margin: 0;
    color: var(--kw-muted);
    font-size: 0.93rem;
  }

  @media (max-width: 820px) {
    .kw-hero,
    .kw-principles {
      grid-template-columns: 1fr;
    }
  }
</style>

<section class="kw-visual" aria-label="Visual model of a Karpathy-style LLM wiki">
  <div class="kw-hero">
    <div>
      <div class="kw-kicker">LLM wiki architecture</div>
      <h2 class="kw-title">Raw first. Synthesis second. Outputs last.</h2>
      <p class="kw-lede">
        A Karpathy-style wiki treats a repository as a working memory for humans and language models. It keeps evidence, durable knowledge, generated deliverables, and operating rules in different layers so future synthesis has provenance.
      </p>
    </div>
    <div class="kw-stack">
      <div class="kw-card" style="--accent: var(--kw-raw)">
        <strong>_raw/</strong>
        <span>Evidence, captures, excerpts, source notes, and scratch thinking.</span>
      </div>
      <div class="kw-card" style="--accent: var(--kw-wiki)">
        <strong>_wiki/</strong>
        <span>Compiled concepts, claims, maps, questions, patterns, and project knowledge.</span>
      </div>
      <div class="kw-card" style="--accent: var(--kw-out)">
        <strong>_outputs/</strong>
        <span>Reports, guides, summaries, decks, and reusable public deliverables.</span>
      </div>
      <div class="kw-card" style="--accent: var(--kw-system)">
        <strong>_system/</strong>
        <span>Schemas, prompts, templates, manifests, lint rules, and workflow controls.</span>
      </div>
    </div>
  </div>

  <div class="kw-flow" role="img" aria-label="Flow from capture to raw source, synthesis, compiled wiki, generated output, and public publishing review">
    <svg viewBox="0 0 1120 430" xmlns="http://www.w3.org/2000/svg">
      <defs>
        <marker id="kw-arrow" markerWidth="12" markerHeight="12" refX="10" refY="6" orient="auto">
          <path d="M2 2 L10 6 L2 10 Z" fill="#6f675c" />
        </marker>
        <filter id="kw-shadow" x="-20%" y="-20%" width="140%" height="140%">
          <feDropShadow dx="0" dy="12" stdDeviation="12" flood-color="#241f1a" flood-opacity="0.12" />
        </filter>
      </defs>

      <rect x="20" y="72" width="180" height="110" rx="24" fill="#fff" stroke="#ded6ca" filter="url(#kw-shadow)" />
      <text x="110" y="118" text-anchor="middle" font-size="18" font-weight="800" fill="#241f1a">Capture</text>
      <text x="110" y="147" text-anchor="middle" font-size="14" fill="#6f675c">clips, notes, links</text>

      <path d="M205 127 H295" stroke="#6f675c" stroke-width="3" marker-end="url(#kw-arrow)" />

      <rect x="300" y="72" width="180" height="110" rx="24" fill="#fff8f1" stroke="#c98a6a" filter="url(#kw-shadow)" />
      <text x="390" y="118" text-anchor="middle" font-size="18" font-weight="800" fill="#8a5a44">_raw</text>
      <text x="390" y="147" text-anchor="middle" font-size="14" fill="#6f675c">source memory</text>

      <path d="M485 127 H575" stroke="#6f675c" stroke-width="3" marker-end="url(#kw-arrow)" />

      <rect x="580" y="72" width="180" height="110" rx="24" fill="#f1faf9" stroke="#74a7ab" filter="url(#kw-shadow)" />
      <text x="670" y="118" text-anchor="middle" font-size="18" font-weight="800" fill="#376f75">Synthesis</text>
      <text x="670" y="147" text-anchor="middle" font-size="14" fill="#6f675c">distill and connect</text>

      <path d="M765 127 H855" stroke="#6f675c" stroke-width="3" marker-end="url(#kw-arrow)" />

      <rect x="860" y="72" width="220" height="110" rx="24" fill="#eef8f8" stroke="#74a7ab" filter="url(#kw-shadow)" />
      <text x="970" y="118" text-anchor="middle" font-size="18" font-weight="800" fill="#376f75">_wiki</text>
      <text x="970" y="147" text-anchor="middle" font-size="14" fill="#6f675c">durable knowledge</text>

      <path d="M970 188 V245" stroke="#6f675c" stroke-width="3" marker-end="url(#kw-arrow)" />

      <rect x="750" y="250" width="220" height="110" rx="24" fill="#fff9e8" stroke="#c7a343" filter="url(#kw-shadow)" />
      <text x="860" y="296" text-anchor="middle" font-size="18" font-weight="800" fill="#8b6f2f">_outputs</text>
      <text x="860" y="325" text-anchor="middle" font-size="14" fill="#6f675c">answers and artifacts</text>

      <path d="M745 305 H635" stroke="#6f675c" stroke-width="3" marker-end="url(#kw-arrow)" />

      <rect x="410" y="250" width="220" height="110" rx="24" fill="#f5f2ff" stroke="#978fd0" filter="url(#kw-shadow)" />
      <text x="520" y="296" text-anchor="middle" font-size="18" font-weight="800" fill="#5e548e">Review gate</text>
      <text x="520" y="325" text-anchor="middle" font-size="14" fill="#6f675c">privacy, quality, links</text>

      <path d="M405 305 H295" stroke="#6f675c" stroke-width="3" marker-end="url(#kw-arrow)" />

      <rect x="70" y="250" width="220" height="110" rx="24" fill="#eef8f8" stroke="#74a7ab" filter="url(#kw-shadow)" />
      <text x="180" y="296" text-anchor="middle" font-size="18" font-weight="800" fill="#376f75">Public atlas</text>
      <text x="180" y="325" text-anchor="middle" font-size="14" fill="#6f675c">curated pages only</text>

      <path d="M520 245 C520 210, 520 205, 520 188" stroke="#5e548e" stroke-width="3" stroke-dasharray="8 8" marker-end="url(#kw-arrow)" />
      <text x="540" y="218" font-size="13" fill="#5e548e">rules from _system</text>
    </svg>

  </div>

  <div class="kw-principles">
    <div class="kw-principle">
      <b>Separate evidence from synthesis</b>
      <p>Raw material stays traceable; wiki pages state what was learned.</p>
    </div>
    <div class="kw-principle">
      <b>Make the graph navigable</b>
      <p>Concepts, claims, maps, and questions link across the knowledge base.</p>
    </div>
    <div class="kw-principle">
      <b>Publish only after review</b>
      <p>Public pages are curated outputs, not automatic mirrors of private notes.</p>
    </div>
  </div>
</section>

## Why this matters

The structure lets an LLM reuse context without flattening everything into one prompt. Raw material remains available for grounding, wiki pages provide durable memory, and system files keep the workflow legible.
