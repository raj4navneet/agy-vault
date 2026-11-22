---
id: PROXY-splice-instrument.settings
type: file_proxy
file_path: "/etc/nixos/config/partial-declarative/splice-instrument.settings"
role: packaging
tags: ["file_proxy", "role/packaging"]
role_router: "[[roles/packaging]]"
last_updated: "2026-10-27"
---
# File Proxy: `splice-instrument.settings`

## Metadata
- **Path on Disk:** `/etc/nixos/config/partial-declarative/splice-instrument.settings`
- **Domain Role:** [[roles/packaging]]
- **Category:** Config Asset Baseline

## Overview & Purpose
Sanitized partial-declarative baseline for Splice Instruments application settings, preserving light theme and low-latency audio preferences.

## Key Interfaces & Exports
- `Injected into Wine prefix AppData on activation`

## Architectural References & Decisions
- [[ADR-004-partial-declarative-harvesting]], [[ADR-007-wine-packaged-applications]]
