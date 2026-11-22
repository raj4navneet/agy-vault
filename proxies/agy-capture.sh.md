---
id: PROXY-agy-capture.sh
type: file_proxy
file_path: "/etc/nixos/scripts/agy-capture.sh"
role: orchestrator
tags: ["file_proxy", "role/orchestrator"]
role_router: "[[roles/orchestrator]]"
last_updated: "2026-10-27"
---
# File Proxy: `agy-capture.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/agy-capture.sh`
- **Domain Role:** [[roles/orchestrator]]
- **Category:** Visual Proof Recorder

## Overview & Purpose
Headless Wayland cage and desktop visual proof recorder. Spawns applications into an isolated headless cage compositor and captures PNG screenshots via grim or MP4 videos via wf-recorder.

## Key Interfaces & Exports
- `-s <out.png>: Capture screenshot`
- `-v <out.mp4>: Record video demo`
- `-c "<cmd>": Command to launch inside cage`
- `-w <sec>: Window render wait duration`

## Architectural References & Decisions
- [[ADR-005-autonomous-orchestrator-and-sandbox]]
- [[TB-007-black-screenshot-cage-erofs]]
