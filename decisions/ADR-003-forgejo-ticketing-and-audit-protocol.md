---
id: ADR-003
type: decision
role: orchestrator
tags: ["role/orchestrator"]
status: accepted
role_router: "[[roles/orchestrator]]"
related_tickets: ["[#1](http://127.0.0.1:3000/agy/nixos-config/issues/1)", "[#2](http://127.0.0.1:3000/agy/nixos-config/issues/2)", "[#12](http://127.0.0.1:3000/agy/nixos-config/issues/12)", "[#13](http://127.0.0.1:3000/agy/nixos-config/issues/13)"]
related_files: ["[[tea-ticket.sh]]", "[[forgejo-sync.sh]]", "[[AGENTS.md]]"]
---
# ADR-003: Local Forgejo Ticketing, Active-Execution Time Tracking & Audit Trail

**Role:** [[roles/orchestrator]]

## Context
Need complete accountability for autonomous coding tasks without losing user conversation context or tracking idle time.

## Decision
1. 'No Ticket, No Code' rule: Never modify system files without an active Forgejo issue.
2. Active-Execution Time Tracking: Stopwatches only run during active command execution. Pause/stop timers when yielding control to user.
3. User Request Audit Trail: Whenever user sends prompt in chat, immediately log to Forgejo under `@navigator` via `tea-ticket log-request`.
4. Run `forgejo-sync` after completion to snapshot SQL dump and push to remotes.
