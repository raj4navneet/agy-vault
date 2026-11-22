---
type: decision
id: "ADR-009"
role: orchestrator
tags: ["role/orchestrator", "dmb/knowledge", "decisions"]
status: accepted
date: 2026-10-27
ticket: "http://127.0.0.1:3000/agy/nixos-config/issues/34"
related_files: ["[[AGENTS.md]]", "[[INDEX]]", "[[vault-sync.sh]]"]
tracebacks: []
---
# ADR-009: Adoption of Directed Memory Bank (DMB) Architecture

## Context & Problem Statement
In [[ADR-001-hybrid-memory]], we introduced a local Obsidian `.vault/` to eliminate mid-session `tea` CLI read loops and maintain persistent context across turns. While this reduced latency from seconds to sub-milliseconds, two key challenges emerged:
1. **Lack of Reading Order / Relevance Routing:** AI agents started sessions without a deterministic sequence of which files to inspect, causing either context starvation or token waste from over-reading.
2. **RAM / Log Contention:** Managing active ticket states in shared append files creates merge conflict churn when multiple agents or human developers write concurrently.

## Decision Drivers
- **Tool-Agnosticism & Human Readability:** Context must reside in plain markdown files navigable by both autonomous agents (Gemini/Antigravity, Claude Code, Cursor) and humans via Obsidian.
- **Strict Reading Order:** Agents must know exactly what to read at session start, during domain work, and during post-flight wrap-up.
- **Multi-Writer Safety:** Concurrent writers (agents, CI, humans) must write to isolated files without git merge conflicts.

## Considered Options
1. *Monolithic Instruction Rule:* Bloat `AGENTS.md` and `GEMINI.md` with full architectural guides and logs. (Rejected: causes token bloat, poor maintainability).
2. *External Vector DB / MCP Server:* Run a live daemon like Mem0/Letta. (Rejected: runtime dependency, network requirements, opaque embedding search).
3. *Directed Memory Bank (DMB) Architecture:* Adopt `pmikutel/directed-memory-bank` specification with Manifest routing, Knowledge/RAM separation, and integration ladders. (Chosen).

## Decision Outcome
We adopted the Directed Memory Bank (DMB) standard inside `.vault/`:
1. **Knowledge Layer (Slow-Changing Truth):**
   - `project/`: System brief (`brief.md`), domain rules (`domain.md`), documentation hygiene (`doc-guide.md`).
   - `technical/`: System patterns (`architecture.md`), tech stack & constraints (`stack.md`).
   - `decisions/`: Immutable ADRs.
   - `proxies/`: 27 structured file proxy summaries for O(1) architectural lookups.
2. **RAM Layer (Fast-Changing Dynamic State):**
   - `tasks/process.md`: Explicit lifecycle rules.
   - `tasks/work/ISSUE-<ID>-<slug>.md`: Isolated, file-per-task in-flight scratchpads.
   - `tasks/log/YYYY-MM-DD-ISSUE-<ID>.md`: Immutable completed ticket records.
3. **Manifest & Relevance Matrix (`INDEX.md`):**
   - Catalogs all files and defines an explicit intent-scoped reading table.
4. **Integration Tier Ladder:**
   - `AGENTS.md` and `GEMINI.md` become thin, high-performance pointers into the memory bank.

## Pros and Cons
### Positive Consequences
- Deterministic context loading: Agents follow a prescribed reading sequence.
- Zero merge conflicts: Isolated per-task scratchpads in `tasks/work/`.
- Deep synergy with Obsidian Graph View and fast Ripgrep backlink queries (`rg "\[\[...\]\]" .vault/`).

### Negative Consequences
- Slightly more directory depth in `.vault/` (mitigated by `INDEX.md` manifest navigation).
