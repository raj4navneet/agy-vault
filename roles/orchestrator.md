---
id: ROLE-ORCHESTRATOR
type: role_router
role: orchestrator
tags: ["role/orchestrator"]
issue_reference: "http://localhost:3000/agy/nixos-config/issues/34"
description: Autonomous IssueOps orchestrator, Bubblewrap sandboxing, FIFO lock queue, mobile bridge, power management, and audit protocol.
---
# Orchestrator Role Context & Knowledge Graph

> **Scope:** Autonomous agent operations, sandboxing, Forgejo webhooks, and phone oversight in `/etc/nixos/orchestrator` and `/etc/nixos/scripts`.

## Functional Domain & Boundary
The `orchestrator` role manages the autonomous agent harness, sandboxed process isolation via Bubblewrap, mobile approval workflows via ntfy, terminal streaming via ttyd over Tailscale, and automated Forgejo ticketing synchronizations.

## Architectural Decision Records (ADRs)
- [[ADR-001-hybrid-memory]] — Separation of Forgejo control plane and local `.vault/` memory plane
- [[ADR-003-forgejo-ticketing-and-audit-protocol]] — Local Forgejo Ticketing, Active-Execution Time Tracking & Audit Trail
- [[ADR-005-autonomous-orchestrator-and-sandbox]] — Autonomous IssueOps Orchestrator, Bubblewrap Sandbox & Mobile Bridge
- [[ADR-006-decoupled-power-and-reboot-pipeline]] — Decoupled Power/Sleep Management & Controlled Reboot TUI
- [[ADR-009-directed-memory-bank]] — Adoption of Directed Memory Bank (DMB) Architecture

## Incident Tracebacks & Root Causes
- [[TB-000-template]] — Template for recording stack traces and module backlinks
- [[TB-001-rebuild-permission-denied]] — Sudoers escalation and rebuild wrapper permission error
- [[TB-002-forgejo-sync-missing-fi]] — Bash syntax error recovery in `forgejo-sync.sh`
- [[TB-003-git-auth-forgejo-sync-prompt]] — Non-interactive Git credential resolution for local Forgejo remotes
- [[TB-005-catastrophic-suspend-hyprland-crash]] — Systemd sleep target masking preventing daemon dropouts
- [[TB-007-black-screenshot-cage-erofs]] — EROFS and missing Documents symlink causing black cage screenshots

## Key File Proxies
- [[agy-sandbox.sh]] — Bubblewrap container isolation wrapper for sandboxed ticket runs.
- [[agy-nixos-claim.sh]] — Concurrency lock manager implementing FIFO lock queue on `ticket-<id>`.
- [[agy-ask.sh]] — Pre-flight dry-build compiler gate and mobile approval broker.
- [[agy-capture.sh]] — Headless Wayland cage and desktop visual proof recorder.
- [[agy-attach.sh]] — Forgejo media asset uploader and mobile ntfy notification dispatcher.
- [[agy-queue.sh]] — Background tmux turn runner managing agent loops.
- [[agy-ttyd.sh]] — WebSockets terminal streaming runner over Tailscale.
- [[orchestrator.py]] — Central IssueOps orchestrator daemon listening on port 8081.
- [[ttyd_manager.py]] — Dynamic process manager for ttyd terminal streaming instances.
- [[tea-ticket.sh]] — CLI automation wrapper for ticketing, time tracking, and request auditing.
- [[forgejo-sync.sh]] — Automated database backup snapshot and git remote synchronization.
- [[vault-sync.sh]] — Knowledge boundary synchronizer between Forgejo and `.vault/`.
- [[reboot-countdown-tui.sh]] — Pre-reboot interactive countdown TUI.
- [[reboot-sync-watcher.py]] — Pre-reboot state validation watcher.
- [[reboot-wrapper.sh]] — High-level reboot pipeline wrapper.
- [[AGENTS.md]] — Canonical system engineering architecture & ticketing protocol specification.
- [[GEMINI.md]] — Gemini CLI session essentials and DMB integration rules.

## Ticket Chronicle Index
- [#1: Bootstrap Local Forgejo & Ticketing Pipeline](http://127.0.0.1:3000/agy/nixos-config/issues/1)
- [#2: Local Forgejo, Ticketing & Phoenix Auto-Sync Chronicle](http://127.0.0.1:3000/agy/nixos-config/issues/2)
- [#3: Ensure nix-rebuild logs are saved to /etc/nixos/logs](http://127.0.0.1:3000/agy/nixos-config/issues/3)
- [#4: Fix nix-rebuild: PermissionDenied](http://127.0.0.1:3000/agy/nixos-config/issues/4)
- [#5: Fix forgejo-sync.sh syntax error](http://127.0.0.1:3000/agy/nixos-config/issues/5)
- [#6: Persistent Git Credentials for forgejo-sync](http://127.0.0.1:3000/agy/nixos-config/issues/6)
- [#7: Remove Hardcoded Placeholder Passwords](http://127.0.0.1:3000/agy/nixos-config/issues/7)
- [#12: Integrate Issue Time Tracking & Conversation Audit Logging](http://127.0.0.1:3000/agy/nixos-config/issues/12)
- [#13: Enforce Active-Execution-Only Time Tracking Policy](http://127.0.0.1:3000/agy/nixos-config/issues/13)
- [#17: Local Mobile Streaming & Control Bridge](http://127.0.0.1:3000/agy/nixos-config/issues/17)
- [#18: Forgejo-Native Autonomous Orchestrator & Self-Sufficient Sandbox](http://127.0.0.1:3000/agy/nixos-config/issues/18)
- [#20: Reboot Countdown TUI](http://127.0.0.1:3000/agy/nixos-config/issues/20)
- [#21: Move orchestrator.py to /etc/nixos](http://127.0.0.1:3000/agy/nixos-config/issues/21)
- [#23: Disable Catastrophic Suspend & Decouple Power Management](http://127.0.0.1:3000/agy/nixos-config/issues/23)
- [#33: Visualize tmux terminal output from phone via ttyd](http://127.0.0.1:3000/agy/nixos-config/issues/33)
- [#34: Initialize Hybrid Obsidian .vault/ Context Graph & Boundary Sync](http://127.0.0.1:3000/agy/nixos-config/issues/34)
- [#35: Render ticket snapshots natively as markdown without code fences](http://127.0.0.1:3000/agy/nixos-config/issues/35)
