---
id: PROJECT-BRIEF
type: knowledge
role: orchestrator
updated: 2026-10-27
tags: ["dmb/knowledge", "project/brief", "role/orchestrator"]
description: "30-second system overview, headline goals, operational guardrails, and architectural boundaries."
---
# Project Brief: AGY Autonomous NixOS Workstation

> **Purpose**: 30-second system overview, headline goals, operational guardrails, and architectural boundaries.
> **When to use**: Load first on every session or when taking in unfamiliar system tasks.

---

## Project Overview

The **AGY Autonomous NixOS Workstation** is a declarative Linux environment and IssueOps development platform tailored for `@navigator`. It merges declarative system configuration via Nix Flakes with an autonomous, agentic task-execution harness.

Coding agents run inside isolated Bubblewrap sandbox containers, claim concurrency locks against `/etc/nixos`, propose changes via dedicated ticket branches, gate critical rebuilds behind compiler dry-build checks and mobile notifications via `ntfy`, and persist institutional knowledge inside an Obsidian-compatible **Directed Memory Bank (DMB)** at `/home/navigator/Documents/obsidian/agy_vault` (`/etc/nixos/.vault`).

---

## Core Goals

### Primary Goal
Deliver a self-sufficient, reproducible, and verifiable engineering environment where autonomous agents and human developers pair-program via IssueOps without context loss.

### Operational Goals
- **Eliminate Session Amnesia**: Maintain persistent architectural rules, active scratchpads, and historical incident tracebacks so agents resume work immediately without re-briefing.
- **Enforce Absolute Accountability**: Every change must originate from a Forgejo ticket ("No Ticket, No Code") with active-execution-only time tracking and user audit trails.
- **Fail-Safe Self-Modification**: Live `/etc/nixos` modifications are strictly concurrency-locked, branch-isolated (`ticket-<ID>`), and compiler-gated before mobile phone sign-off.

### Technical Goals
- **Clean Architecture Purity**: Segregate host-level NixOS modules (`system/`), user-level Home Manager suites (`home/`), raw static assets (`config/`), and automation scripts (`scripts/`).
- **Redis Descriptive Naming**: Ban ambiguous abbreviations; enforce explicit verb-noun naming and interrogative booleans (`is_active`, `enable_gui`).
- **Low-Latency Creative Audio**: Pro-audio orchestration using PipeWire, yabridge, Wine-GE, and declarative asset harvesting for Windows DAW tools (Splice, Affinity).

---

## Success Criteria & Guardrails

- **Zero Zombie Code**: Immediate deletion of commented-out blocks; git preserves history.
- **Sub-10ms Context Lookup**: Local 1-hop backlink graph queries (`rg "\[\[Target\]\]" .vault/`) replace slow web or API lookups.
- **Clean Commit Chronicles**: 100% of commits linked to Forgejo tickets with commit trailers (`Closes #<ID>` / `Refs #<ID>`).
- **Multi-Writer Safety**: File-per-item structure for tickets, logs, tracebacks, and ADRs avoids merge collisions between human and agent writers.

---

## Key Stakeholders

- **`@navigator`**: Human operator, lead architect, and final arbiter for hardware, sudo escalations, and mobile approvals.
- **`@agy`**: Autonomous AI coding assistant, issue runner, and maintainer of system modules and memory bank files.

---

## Project Scope

### In Scope
- Host NixOS configurations under `/etc/nixos/system/`.
- User desktop environment (Hyprland, Waybar, Foot/Kitty) under `/etc/nixos/home/`.
- Unprocessed configuration assets under `/etc/nixos/config/`.
- Autonomous orchestrator daemon and automation scripts under `/etc/nixos/orchestrator/` and `/etc/nixos/scripts/`.
- Directed Memory Bank knowledge and RAM state under `/etc/nixos/.vault/`.

### Out of Scope
- Imperative package installations (`nix-env -i`, manual binaries in `/usr/local/bin`).
- Direct commits to the `main` branch without ticket locks and review.
- Long narrative essays or debugging logs inside Nix expressions or script files.

---

## Knowledge Graph Cross-References
- Root Router: [[INDEX]]
- Domain Models: [[project/domain]]
- Documentation Hygiene: [[project/doc-guide]]
- Technology Stack: [[technical/stack]]
- System Architecture: [[technical/architecture]]
- Active Context: [[active-context]]
