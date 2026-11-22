---
id: PROXY-agy-ask.sh
type: file_proxy
file_path: "/etc/nixos/scripts/agy-ask.sh"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `agy-ask.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/agy-ask.sh`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Approval Broker & Compiler Gate

## Overview & Purpose
Pre-flight dry-build compiler check and mobile approval broker. Verifies NixOS derivations compile without root privileges before submitting requests to the orchestrator for mobile phone approval via ntfy.

## Key Interfaces & Exports
- `agy-ask <ticket_id> "<command>": Request execution approval`
- `Integrates with orchestrator /api/ask/create and /api/host-exec`

## Architectural References & Decisions
- [[ADR-005-autonomous-orchestrator-and-sandbox]]
