---
id: PROXY-ttyd_manager.py
type: file_proxy
file_path: "/etc/nixos/orchestrator/ttyd_manager.py"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `ttyd_manager.py`

## Metadata
- **Path on Disk:** `/etc/nixos/orchestrator/ttyd_manager.py`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Process Manager

## Overview & Purpose
Dynamic process manager for ttyd instances. Allocates ports, spawns streams on demand for active ticket turns, and prunes orphaned processes.

## Key Interfaces & Exports
- `ensure_ttyd(ticket_id): Allocate port and start stream`
- `stop_ttyd(ticket_id): Terminate active stream`

## Architectural References & Decisions
- [[ADR-005-autonomous-orchestrator-and-sandbox]]
