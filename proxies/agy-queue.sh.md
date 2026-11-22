---
id: PROXY-agy-queue.sh
type: file_proxy
file_path: "/etc/nixos/scripts/agy-queue.sh"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `agy-queue.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/agy-queue.sh`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Turn Queue Runner

## Overview & Purpose
Spawns and manages autonomous agent execution turns inside dedicated background tmux sessions, tracking lifecycle status and persisting run logs.

## Key Interfaces & Exports
- `agy-queue <ticket_id>: Launch queue runner for issue`
- `Session name format: agy-ticket-<id>`

## Architectural References & Decisions
- [[ADR-005-autonomous-orchestrator-and-sandbox]]
