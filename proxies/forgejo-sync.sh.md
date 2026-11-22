---
id: PROXY-forgejo-sync.sh
type: file_proxy
file_path: "/etc/nixos/scripts/forgejo-sync.sh"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `forgejo-sync.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/forgejo-sync.sh`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Database Dump & Sync Utility

## Overview & Purpose
Snapshots the local Forgejo SQLite database into /etc/nixos/forgejo-state/forgejo-data.sql and pushes repository commits to local and remote Git remotes.

## Key Interfaces & Exports
- `forgejo-sync: Execute database export and git push`

## Architectural References & Decisions
- [[ADR-003-forgejo-ticketing-and-audit-protocol]]
