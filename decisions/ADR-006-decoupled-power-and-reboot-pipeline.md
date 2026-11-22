---
id: ADR-006
type: decision
role: orchestrator
tags: ["role/orchestrator"]
status: accepted
role_router: "[[roles/orchestrator]]"
related_tickets: ["[#20](http://127.0.0.1:3000/agy/nixos-config/issues/20)", "[#23](http://127.0.0.1:3000/agy/nixos-config/issues/23)"]
related_files: ["[[reboot-countdown-tui.sh]]", "[[reboot-sync-watcher.py]]", "[[reboot-wrapper.sh]]"]
---
# ADR-006: Decoupled Power/Sleep Management & Controlled Reboot TUI

**Role:** [[roles/orchestrator]]

## Context
Automatic desktop sleep was causing catastrophic drops of long-running Nix builds, tmux runners, and network connectivity.

## Decision
1. Mask systemd `sleep.target`, `suspend.target`, `hibernate.target`, and `hybrid-sleep.target` to prevent OS-level suspension.
2. Implement controlled reboot pipeline with terminal countdown TUI (`reboot-countdown-tui.sh`) and sync watchers (`reboot-sync-watcher.py`).
