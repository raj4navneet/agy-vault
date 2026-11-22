---
id: PROXY-GEMINI.md
type: file_proxy
file_path: "/etc/nixos/GEMINI.md"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `GEMINI.md`

## Metadata
- **Path on Disk:** `/etc/nixos/GEMINI.md`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Architecture & Engineering Protocol / DMB Shim

## Overview & Purpose
Gemini session essentials and thin DMB integration shim. Delegates context discovery to [[INDEX]], outlines essential commands, active time tracking, command explanations, and code purity baselines.

## Key Interfaces & Exports
- `Governs all Gemini agent sessions, command explanations, and DMB context loading`

## Architectural References & Decisions
- [[ADR-001-hybrid-memory]], [[ADR-002-clean-architecture-and-purity]], [[ADR-003-forgejo-ticketing-and-audit-protocol]]
