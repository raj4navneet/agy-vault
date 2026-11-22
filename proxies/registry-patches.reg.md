---
id: PROXY-registry-patches.reg
type: file_proxy
file_path: "/home/navigator/dev/SpliceINSTRUMENT-nix/registry-patches.reg"
role: packaging
tags: ["file_proxy", "role/packaging"]
role_router: "[[roles/packaging]]"
last_updated: "2026-10-27"
---
# File Proxy: `registry-patches.reg`

## Metadata
- **Path on Disk:** `/home/navigator/dev/SpliceINSTRUMENT-nix/registry-patches.reg`
- **Domain Role:** [[roles/packaging]]
- **Category:** Wine Registry Patch

## Overview & Purpose
Registry patches for Wine audio application optimizations including low-latency WASAPI buffer overrides and font smoothing.

## Key Interfaces & Exports
- `Applied by Wine launcher scripts`

## Architectural References & Decisions
- [[ADR-007-wine-packaged-applications]]
