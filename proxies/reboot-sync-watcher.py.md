---
id: PROXY-reboot-sync-watcher.py
type: file_proxy
file_path: "/etc/nixos/scripts/reboot-sync-watcher.py"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `reboot-sync-watcher.py`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/reboot-sync-watcher.py`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Pre-Reboot Sync Guard

## Overview & Purpose
Pre-reboot state validation script. Ensures all uncommitted git changes, Forgejo database dumps, and active agent turns are flushed before permitting system restart.

## Key Interfaces & Exports
- `Verifies git status in /etc/nixos`
- `Verifies SQLite database dump state`

## Architectural References & Decisions
- [[ADR-006-decoupled-power-and-reboot-pipeline]]
