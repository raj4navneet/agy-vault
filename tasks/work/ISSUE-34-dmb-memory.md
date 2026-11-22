---
type: work
id: 34
role: orchestrator
tags: ["role/orchestrator", "dmb/ram", "tasks/work"]
ticket: "http://127.0.0.1:3000/agy/nixos-config/issues/34"
status: in-progress
created: 2026-10-27T19:35:00+11:00
updated: 2026-10-27T19:44:00+11:00
related_files: ["[[AGENTS.md]]", "[[vault-sync.sh]]", "[[INDEX]]"]
decisions: ["[[ADR-001-hybrid-memory]]", "[[ADR-009-directed-memory-bank]]"]
tracebacks: []
---
# In-Flight Task: ISSUE-34 Directed Memory Bank (DMB) Integration

## Goal
Improve the AGY agent memory architecture and Obsidian `.vault/` graph by implementing the Directed Memory Bank (DMB) pattern (`pmikutel/directed-memory-bank`):
1. Establish a strict reading order and relevance routing matrix in `INDEX.md`.
2. Segregate the Knowledge Layer (`project/`, `technical/`, `decisions/`, `proxies/`) from the RAM Layer (`tasks/work/`, `tasks/log/`).
3. Implement multi-writer safe task management with dedicated in-flight scratchpads and completed log archival.
4. Establish thin, high-performance integration ladders in `AGENTS.md` and `GEMINI.md`.

## Active Progress & Execution Log
- [x] Researched `pmikutel/directed-memory-bank` specification, manifest schema, and Knowledge/RAM architecture.
- [x] Started active execution timer via `tea-ticket start-timer 34`.
- [x] Ingested latest Forgejo state via `./scripts/vault-sync.sh pull 34`.
- [x] Posted formal Investigation & Architectural Plan comment to Forgejo Ticket #34.
- [x] Scaffolding DMB Knowledge Layer:
  - [x] Created `.vault/project/brief.md` (30-second system overview).
  - [x] Created `.vault/project/domain.md` (domain boundaries, roles, lifecycle).
  - [x] Created `.vault/project/doc-guide.md` (markdown hygiene, size limits, frontmatter schema).
  - [x] Created `.vault/technical/architecture.md` (Clean Architecture, Flask modularity, Redis naming, DMB design).
  - [x] Created `.vault/technical/stack.md` (authoritative software stack & constraints).
- [x] Scaffolding DMB RAM Layer:
  - [x] Created `.vault/tasks/process.md` (RAM lifecycle & multi-writer protocol).
  - [x] Created `.vault/tasks/work/ISSUE-34-dmb-memory.md` (this active work item).
- [x] Created `ADR-009-directed-memory-bank.md` in `.vault/decisions/`.
- [x] Refactored `.vault/INDEX.md` as DMB Manifest & Runtime Routing Table.
- [x] Updated `scripts/vault-sync.sh` with DMB pull/push task workflow.
- [x] Verified 1-hop backlink queries with Ripgrep (`0.002s` traversal).
- [x] Captured visual verification (`obsidian /home/navigator/agy-workspaces/ticket-34/.vault`) via headless Wayland cage to `proof.png` and attached to Ticket #34.
- [x] Committed changes to branch `ticket-34` (`c447e24`) and pushed to `origin/ticket-34`.

## Resolution Summary
- **Commit:** c447e24 (`feat(agent-memory): adopt directed memory bank pattern with manifest routing and knowledge/ram layers (Refs #34)`)
- **Key Enhancements:**
  1. **Manifest & Intent-Scoped Reading Matrix (`.vault/INDEX.md`):** Transformed top-level index into a full DMB manifest prescribing deterministic reading sequences for session start, domain engineering, incident debugging, and post-flight archival.
  2. **Knowledge vs. RAM Layer Segregation:**
     - **Knowledge Layer:** Created `project/brief.md` (30s system overview), `project/domain.md` (role boundaries and lifecycle), `project/doc-guide.md` (markdown hygiene & frontmatter standards), `technical/architecture.md`, and `technical/stack.md`.
     - **RAM Layer:** Created `tasks/process.md` and dedicated file-per-task scratchpads in `tasks/work/` with automated graduation to `tasks/log/`.
  3. **Multi-Writer Safety:** Converted task tracking from shared append files to isolated per-task scratchpads, preventing git merge conflicts between concurrent agents and humans.
  4. **Boundary Sync Upgrade (`scripts/vault-sync.sh`):** Integrated DMB task pull/push automation, linking `active-context.md` directly to active work items and archiving completed work on push.
  5. **Architectural Decision Record:** Codified principles in `ADR-009-directed-memory-bank.md`.
  6. **Visual Verification:** Rendered Obsidian with the new DMB vault into a headless Wayland cage, captured `proof.png`, and attached it to Ticket #34.
- **Rollback Instructions:** `git revert c447e24`
