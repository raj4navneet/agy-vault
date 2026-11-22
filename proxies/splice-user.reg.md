---
id: PROXY-splice-user.reg
type: file_proxy
file_path: "/etc/nixos/config/partial-declarative/splice-user.reg"
role: packaging
tags: ["file_proxy", "role/packaging"]
role_router: "[[roles/packaging]]"
last_updated: "2026-10-27"
---
# File Proxy: `splice-user.reg`

## Metadata
- **Path on Disk:** `/etc/nixos/config/partial-declarative/splice-user.reg`
- **Domain Role:** [[roles/packaging]]
- **Category:** Wine Registry Baseline

## Overview & Purpose
Sanitized partial-declarative Wine registry hive for Splice Instruments tuning display resolution, WebView2 environment, and WASAPI buffer sizes.

## Key Interfaces & Exports
- `Merged into user.reg on activation`

## Architectural References & Decisions
- [[ADR-004-partial-declarative-harvesting]], [[ADR-007-wine-packaged-applications]]
