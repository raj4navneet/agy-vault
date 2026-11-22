---
id: PROXY-agy-attach.sh
type: file_proxy
file_path: "/etc/nixos/scripts/agy-attach.sh"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `agy-attach.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/agy-attach.sh`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Forgejo Media Uploader

## Overview & Purpose
Forgejo asset uploader and mobile demo notifier. Uploads screenshots and videos directly to Forgejo issue threads via REST API and triggers push notifications to phone via ntfy.

## Key Interfaces & Exports
- `-t <ticket_id>: Forgejo issue ID`
- `-f <file_path>: Image or video asset path`
- `-c "<caption text>": Attachment caption`

## Architectural References & Decisions
- [[ADR-005-autonomous-orchestrator-and-sandbox]]
- [[TB-007-black-screenshot-cage-erofs]]
