---
id: PROXY-reboot-wrapper.sh
type: file_proxy
file_path: "/etc/nixos/scripts/reboot-wrapper.sh"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `reboot-wrapper.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/reboot-wrapper.sh`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Reboot Pipeline Script

## Overview & Purpose
High-level reboot pipeline executing reboot-sync-watcher.py and reboot-countdown-tui.sh before invoking systemctl reboot.

## Key Interfaces & Exports
- `reboot-wrapper.sh: Controlled reboot execution`

## Architectural References & Decisions
- [[ADR-006-decoupled-power-and-reboot-pipeline]]
