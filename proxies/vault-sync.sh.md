---
id: PROXY-vault-sync.sh
type: file_proxy
file_path: "/etc/nixos/scripts/vault-sync.sh"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `vault-sync.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/vault-sync.sh`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Knowledge Boundary Synchronizer

## Overview & Purpose
Synchronizes Forgejo issue context into local .vault/ working memory notes, enforcing zero mid-session tea read loops via single pre-flight pull and single post-flight push boundaries.

## Key Interfaces & Exports
- `vault-sync.sh pull <issue_id>: Pull issue into .vault/tickets/ISSUE-<id>.md`
- `vault-sync.sh push <issue_id>: Push Post-Flight Summary to Forgejo`

## Architectural References & Decisions
- [[ADR-001-hybrid-memory]]
