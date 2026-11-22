---
title: Refine Obsidian logic using Directed Memory Bank (DMB) patterns
ticket_id: 36
status: active
priority: high
branch: ticket-36
started: 2026-10-27
updated: 2026-10-27
role: orchestrator
tags: ["role/orchestrator", "vault", "dmb"]
---
# Ticket #36: Refine Obsidian logic using Directed Memory Bank (DMB)

## In-Flight Working Scratchpad

### Objective
Refactor `.vault/` with DMB conventions:
- Knowledge / RAM layer split.
- Core knowledge documents (`project/brief.md`, `project/domain.md`, `project/doc-guide.md`, `technical/stack.md`, `technical/architecture.md`).
- Operation-scoped discovery matrix in `INDEX.md`.
- Thin integration shims in `AGENTS.md` / `GEMINI.md`.
- Seamless compatibility with `vault-sync.sh`.

### Progress Checklist
- [x] Claimed `/etc/nixos` lock on branch `ticket-36`.
- [x] Posted investigation and plan comment to Ticket #36.
- [x] Created `project/brief.md`.
- [x] Created `project/domain.md`.
- [x] Created `project/doc-guide.md`.
- [x] Created `technical/stack.md`.
- [x] Created `technical/architecture.md`.
- [x] Created `tasks/process.md`.
- [x] Initialized `tasks/work/` and `tasks/log/`.
- [ ] Refactor `.vault/INDEX.md` with operation discovery matrix.
- [ ] Update `active-context.md` for ticket 36.
- [ ] Update `scripts/vault-sync.sh` to support DMB tasks layer.
- [ ] Refactor `GEMINI.md` and `AGENT.md` / `AGENTS.md` integration shims.
- [ ] Verification and dry-build check.
