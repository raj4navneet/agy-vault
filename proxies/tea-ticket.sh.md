---
id: PROXY-tea-ticket.sh
type: file_proxy
file_path: "/etc/nixos/scripts/tea-ticket.sh"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `tea-ticket.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/tea-ticket.sh`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Ticketing Protocol CLI

## Overview & Purpose
CLI wrapper for tea enforcing the AGY engineering protocol. Manages ticket creation, active-execution stopwatch time tracking, and user prompt audit logging.

## Key Interfaces & Exports
- `tea-ticket create --title <t> --description <d>`
- `tea-ticket start-timer <id>`
- `tea-ticket stop-timer <id>`
- `tea-ticket log-request <id> <text>`

## Architectural References & Decisions
- [[ADR-003-forgejo-ticketing-and-audit-protocol]]
