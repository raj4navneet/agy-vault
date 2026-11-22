---
id: PROXY-agy-nixos-claim.sh
type: file_proxy
file_path: "/etc/nixos/scripts/agy-nixos-claim.sh"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `agy-nixos-claim.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/agy-nixos-claim.sh`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Concurrency Lock Manager

## Overview & Purpose
Concurrency lock manager for /etc/nixos. Implements a FIFO queue granting exclusive write locks to autonomous agents on ticket-specific git branches to prevent race conditions.

## Key Interfaces & Exports
- `agy-nixos-claim <ticket_id>: Claim exclusive lock and checkout ticket-<id>`
- `Lock state: /tmp/nixos-claim.lock`

## Architectural References & Decisions
- [[ADR-005-autonomous-orchestrator-and-sandbox]]
