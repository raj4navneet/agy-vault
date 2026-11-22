---
id: PROXY-agy-sandbox.sh
type: file_proxy
file_path: "/etc/nixos/scripts/agy-sandbox.sh"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `agy-sandbox.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/agy-sandbox.sh`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Sandbox Container Script

## Overview & Purpose
Bubblewrap process isolation wrapper. Executes commands inside a containerized sandbox with a read-only root filesystem, restricted device and network access, and a read-write scratch workspace per ticket.

## Key Interfaces & Exports
- `--workspace <path>: Set ticket workspace directory`
- `--project <path>: Whitelist project repository path`
- `--net: Enable host network access`
- `--policy <file>: Load dynamic JSON security policy`

## Architectural References & Decisions
- [[ADR-005-autonomous-orchestrator-and-sandbox]]
- [[TB-007-black-screenshot-cage-erofs]]
