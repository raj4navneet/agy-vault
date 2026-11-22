---
id: PROXY-reboot-countdown-tui.sh
type: file_proxy
file_path: "/etc/nixos/scripts/reboot-countdown-tui.sh"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `reboot-countdown-tui.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/reboot-countdown-tui.sh`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Terminal UI Tool

## Overview & Purpose
Terminal countdown UI displaying a visible countdown and abort prompt before triggering system reboots.

## Key Interfaces & Exports
- `reboot-countdown-tui.sh <seconds>: Display countdown with abort key`

## Architectural References & Decisions
- [[ADR-006-decoupled-power-and-reboot-pipeline]]
