---
id: ADR-001
type: decision
role: orchestrator
tags: ["role/orchestrator"]
status: accepted
role_router: "[[roles/orchestrator]]"
related_files: ["[[AGENTS.md]]", "[[vault-sync.sh]]"]
---
# ADR-001: Hybrid Forgejo + Obsidian Memory Architecture

**Role:** [[roles/orchestrator]]

## Context
Running `tea issues view` and `tea issues list` repeatedly during agent execution wastes tokens and adds CLI latency.

## Decision
1. **Forgejo** is strictly the human/mobile control plane.
2. **`.vault/`** is the agent's working memory during task execution.
3. Every traceback or bug found must be logged in `.vault/tracebacks/` with `filename.ext` and `ISSUE-<ID>` backlinks.
