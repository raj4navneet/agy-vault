---
id: ADR-005
type: decision
role: orchestrator
tags: ["role/orchestrator"]
status: accepted
role_router: "[[roles/orchestrator]]"
related_tickets: ["[#17](http://127.0.0.1:3000/agy/nixos-config/issues/17)", "[#18](http://127.0.0.1:3000/agy/nixos-config/issues/18)", "[#21](http://127.0.0.1:3000/agy/nixos-config/issues/21)", "[#33](http://127.0.0.1:3000/agy/nixos-config/issues/33)"]
related_files: ["[[orchestrator.py]]", "[[agy-sandbox.sh]]", "[[agy-nixos-claim.sh]]", "[[agy-ask.sh]]", "[[ttyd_manager.py]]"]
---
# ADR-005: Autonomous IssueOps Orchestrator, Bubblewrap Sandbox & Mobile Bridge

**Role:** [[roles/orchestrator]]

## Context
Autonomous agents require isolated execution environments, FIFO access to system flake edits, and seamless mobile oversight.

## Decision
1. Run `agy-orchestrator.py` daemon listening on port 8081 for local IPC and Forgejo webhooks.
2. Sandbox agents using Bubblewrap (`agy-sandbox.sh`) with read-only root and per-ticket workspaces (`~/agy-workspaces/ticket-<id>`).
3. Gate `/etc/nixos` modifications behind a FIFO lock queue (`agy-nixos-claim.sh`).
4. Dispatch ntfy alerts with 1-tap mobile action buttons (Approve, Reject, Pause, Resume) and stream live tmux sessions via `ttyd` over Tailscale.
