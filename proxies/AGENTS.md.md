---
id: PROXY-AGENTS.md
type: file_proxy
file_path: "/etc/nixos/AGENT.md"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `AGENTS.md`

## Metadata
- **Path on Disk:** `/etc/nixos/AGENT.md`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Architecture & Engineering Protocol

## Overview & Purpose
Canonical system architecture and ticketing protocol specification. Mandates Redis naming, Flask modularity, Clean Architecture, Go boringness, 200-line limits, and strict No Ticket, No Code rules.

## Key Interfaces & Exports
- `Governs all agent sessions, code edits, and ticketing lifecycles`

## Architectural References & Decisions
- [[ADR-001-hybrid-memory]], [[ADR-002-clean-architecture-and-purity]], [[ADR-003-forgejo-ticketing-and-audit-protocol]]
