---
type: Concept
title: ObjectGraph
description: A visual explanation of ObjectGraph as a Markdown-compatible, typed knowledge graph format for agent-native document traversal.
visibility: public
status: active
tags:
  - concepts
  - objectgraph
  - agentic-documents
  - knowledge-architecture
sources:
  - https://arxiv.org/pdf/2604.27820
---

# ObjectGraph

ObjectGraph is a proposed document format for the agentic era: instead of treating a document as one long string to inject into an LLM context window, it treats the document as a typed, directed knowledge graph that an agent can traverse.

Source: [ObjectGraph: From Document Injection to Knowledge Traversal](https://arxiv.org/pdf/2604.27820) by Mohit Dubey / Open Gigantic.

<section class="og-visual" aria-label="ObjectGraph concept map">
  <div class="og-hero">
    <div class="og-hero-copy">
      <div class="og-kicker">Agent-native document format</div>
      <h2 class="og-title">Stop injecting documents. Traverse knowledge.</h2>
      <p class="og-lede">
        ObjectGraph reframes a Markdown-like document as a set of addressable nodes, typed edges, role scopes, and executable assertions. The agent reads a tiny index first, then resolves only the nodes needed for the current task.
      </p>
    </div>
    <div class="og-scoreboard" aria-label="Reported ObjectGraph headline claims">
      <div class="og-stat og-stat-primary">
        <span>reported token reduction</span>
        <strong>60-95%</strong>
      </div>
      <div class="og-stat">
        <span>query primitives</span>
        <strong>2</strong>
      </div>
      <div class="og-stat">
        <span>required properties</span>
        <strong>6/6</strong>
      </div>
      <div class="og-stat">
        <span>transpiler fidelity reported</span>
        <strong>98.7%</strong>
      </div>
    </div>
  </div>
  <div class="og-problem" aria-label="Document consumption problem">
    <div class="og-panel og-panel-dark">
      <div class="og-label">Current Markdown consumption</div>
      <h3>Full-read by default</h3>
      <div class="og-doc-strip" aria-hidden="true">
        <span></span><span></span><span></span><span></span><span></span><span></span>
      </div>
      <p>An agent cannot know which section matters without reading the document. So runbooks, skills, plans, and docs get injected wholesale.</p>
      <ul class="og-mini-list">
        <li>Token inflation from irrelevant sections.</li>
        <li>Context compounding across multi-turn loops.</li>
        <li>Role blindness: every agent sees the same text.</li>
      </ul>
    </div>
    <div class="og-problem-arrow" aria-hidden="true">-></div>
    <div class="og-panel og-panel-bright">
      <div class="og-label">ObjectGraph consumption</div>
      <h3>Index first, node second</h3>
      <div class="og-node-grid" aria-hidden="true">
        <span class="og-node-dot og-node-hot"></span><span class="og-node-line"></span><span class="og-node-dot"></span><span class="og-node-line"></span><span class="og-node-dot"></span><span class="og-node-dot"></span><span class="og-node-line"></span><span class="og-node-dot og-node-hot"></span>
      </div>
      <p>The file exposes a compact routing table. The agent selects node IDs, then resolves full context plus required dependencies.</p>
      <ul class="og-mini-list">
        <li>Retrieve only relevant semantic units.</li>
        <li>Traverse explicit dependency edges.</li>
        <li>Filter nodes by consumer role.</li>
      </ul>
    </div>
  </div>
  <div class="og-anatomy" aria-label="ObjectGraph file anatomy">
    <div class="og-section-head">
      <div class="og-label">File anatomy</div>
      <h3>A document becomes a graph manifest plus nodes.</h3>
      <p>The paper's key move is not a database. It is a plain-text format that keeps enough structure inside the file for agents to route before reading.</p>
    </div>
    <div class="og-code-card" aria-label="ObjectGraph syntax sketch">
      <div class="og-code-bar"><span></span><span></span><span></span><strong>deployment.og</strong></div>
      <div class="og-code-body">
        <div><b>::meta</b> title, version, domain, scope <b>::end</b></div>
        <div><b>::schema</b> node-types, edge-types, roles <b>::end</b></div>
        <div><b>::index</b> id | type | scope | confidence | keywords <b>::end</b></div>
        <div><b>::node[id=install type=step scope=all]</b></div>
        <div class="og-indent"><b>::dense</b> python | pip | venv | requirements <b>::end</b></div>
        <div class="og-indent"><b>::full</b> complete prose explanation <b>::end</b></div>
        <div class="og-indent"><b>::steps</b> ordered execution path <b>::end</b></div>
        <div class="og-indent"><b>::edges</b> ->[:requires] configure <b>::end</b></div>
        <div><b>::end</b> # install</div>
      </div>
    </div>
  </div>
  <div class="og-passages" aria-label="Progressive disclosure model">
    <div class="og-pass og-pass-one">
      <small>Pass 1</small>
      <strong>Index</strong>
      <span>Read metadata and routing table. Decide which node IDs look relevant.</span>
      <em>fixed, tiny cost</em>
    </div>
    <div class="og-pass og-pass-two">
      <small>Pass 2</small>
      <strong>Dense</strong>
      <span>Read compressed node summaries for planning, routing, and triage.</span>
      <em>roughly keywords per node</em>
    </div>
    <div class="og-pass og-pass-three">
      <small>Pass 3</small>
      <strong>Full</strong>
      <span>Read prose, code, steps, warnings, tables, and assertions only when execution needs them.</span>
      <em>full fidelity on demand</em>
    </div>
  </div>
  <div class="og-protocol" aria-label="LLM-native ObjectGraph query protocol">
    <div class="og-section-head">
      <div class="og-label">Two-primitive protocol</div>
      <h3>The interface is deliberately small.</h3>
      <p>The paper proposes two primitives that can be exposed as MCP tools or function calls. The LLM still reasons semantically, but the file stops requiring full injection.</p>
    </div>
    <div class="og-protocol-grid">
      <div class="og-call">
        <small>1</small>
        <strong>search_index(file, query, role)</strong>
        <span>Returns scoped candidate node IDs from the index. Role filtering happens before content is revealed.</span>
      </div>
      <div class="og-call-arrow" aria-hidden="true">-></div>
      <div class="og-call">
        <small>2</small>
        <strong>resolve_context(file, node_ids)</strong>
        <span>Returns selected nodes plus required dependency nodes reached through typed edges.</span>
      </div>
    </div>
  </div>
  <div class="og-matrix" aria-label="Six required properties satisfied by ObjectGraph">
    <div class="og-matrix-head">
      <div class="og-label">Six properties</div>
      <h3>What agent-native documents need at format level.</h3>
    </div>
    <div class="og-property"><b>P1</b><strong>Query-addressable index</strong><span>Map task intent to candidate node IDs before loading content.</span></div>
    <div class="og-property"><b>P2</b><strong>Layered compression</strong><span>Encode dense summaries and full detail as separate native layers.</span></div>
    <div class="og-property"><b>P3</b><strong>Typed dependency graph</strong><span>Declare requires, precedes, see-also, supersedes, and related edges.</span></div>
    <div class="og-property"><b>P4</b><strong>Role-scoped access</strong><span>Serve different node sets to orchestrators, workers, and monitors.</span></div>
    <div class="og-property"><b>P5</b><strong>Executable assertions</strong><span>Store validation checks, retry limits, and escalation paths in the document.</span></div>
    <div class="og-property"><b>P6</b><strong>Human readability</strong><span>Stay authorable as plain text and backward-compatible with Markdown.</span></div>
  </div>
  <div class="og-roles" aria-label="Role-scoped access examples">
    <div class="og-role-card">
      <small>orchestrator</small>
      <strong>Can resolve secrets and privileged runbook steps.</strong>
      <span>Example: real Vault lookup for production API keys.</span>
    </div>
    <div class="og-role-card">
      <small>worker</small>
      <strong>Receives safe abstractions and requested capabilities.</strong>
      <span>Example: ask orchestrator for credentials instead of seeing them.</span>
    </div>
    <div class="og-role-card">
      <small>readonly</small>
      <strong>Can inspect status without operational authority.</strong>
      <span>Example: view summaries, warnings, and public assertions only.</span>
    </div>
  </div>
  <div class="og-takeaways" aria-label="ObjectGraph interpretation and caveats">
    <div class="og-takeaway og-takeaway-main">
      <div class="og-label">Interpretation</div>
      <h3>The real claim is architectural.</h3>
      <p>ObjectGraph argues that agent context waste is not only a retrieval problem. It is a document-format problem: the file itself should expose addressability, dependencies, access scope, validation, and update metadata.</p>
    </div>
    <div class="og-takeaway">
      <strong>Best fit</strong>
      <span>Skill files, operational runbooks, execution plans, technical docs, and maintained knowledge bases.</span>
    </div>
    <div class="og-takeaway">
      <strong>Open risk</strong>
      <span>Cross-file federation, governance, adversarial indexes, and dialect fragmentation still need real-world proof.</span>
    </div>
  </div>
</section>

## Why It Matters

ObjectGraph is useful as a design lens even if the exact `.og` format never becomes a standard. It names a real failure mode in agent systems: agents are often forced to consume documents as linear context blobs even when the task only needs a small, role-specific slice.

The important shift is from document injection to document traversal. A document can carry its own routing table, dependency graph, access scope, and validation logic. That makes the file itself more like a lightweight knowledge substrate than a passive page.

## Practical Reading

- The strongest idea is the **index-first read path**: agents should inspect a compact map before reading the full document.
- The most operational idea is **role-scoped access**: the same source file can expose different nodes to orchestrators, workers, and monitors.
- The most underused idea is **executable assertions**: validation and retry paths should live near the procedure they check.
- The biggest unresolved issue is **federation**: one file can be traversed cleanly, but real knowledge systems need safe cross-file edges.

## Source

- Mohit Dubey / Open Gigantic, [ObjectGraph: From Document Injection to Knowledge Traversal](https://arxiv.org/pdf/2604.27820).
