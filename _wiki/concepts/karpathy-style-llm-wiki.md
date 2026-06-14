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
