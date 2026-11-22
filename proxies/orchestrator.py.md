---
id: PROXY-orchestrator.py
type: file_proxy
file_path: "/etc/nixos/orchestrator/orchestrator.py"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `orchestrator.py`

## Metadata
- **Path on Disk:** `/etc/nixos/orchestrator/orchestrator.py`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Autonomous Daemon Service

## Overview & Purpose
Central IssueOps orchestrator daemon listening on port 8081. Handles Forgejo webhook events, manages ticket queues, handles mobile approval gates, and dispatches host executions.

## Key Interfaces & Exports
- `HTTP server on 127.0.0.1:8081`
- `Endpoints: /api/ask/create, /api/ask/status/<id>, /api/host-exec, /api/webhooks`

## Architectural References & Decisions
- [[ADR-005-autonomous-orchestrator-and-sandbox]]
