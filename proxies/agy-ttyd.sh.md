---
id: PROXY-agy-ttyd.sh
type: file_proxy
file_path: "/etc/nixos/scripts/agy-ttyd.sh"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `agy-ttyd.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/agy-ttyd.sh`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Live Terminal Streaming Runner

## Overview & Purpose
Starts a web-based terminal stream via ttyd attached to the active tmux agent session, restricted to Tailscale network interface for secure mobile oversight.

## Key Interfaces & Exports
- `agy-ttyd.sh <ticket_id> <port>: Stream tmux session`
- `Port range: 7700-7799`

## Architectural References & Decisions
- [[ADR-005-autonomous-orchestrator-and-sandbox]]
