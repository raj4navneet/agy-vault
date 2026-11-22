---
id: PROXY-splice-instrument.sh
type: file_proxy
file_path: "/home/navigator/dev/SpliceINSTRUMENT-nix/runner/splice-instrument.sh"
role: packaging
tags: ["file_proxy", "role/packaging"]
role_router: "[[roles/packaging]]"
last_updated: "2026-10-27"
---
# File Proxy: `splice-instrument.sh`

## Metadata
- **Path on Disk:** `/home/navigator/dev/SpliceINSTRUMENT-nix/runner/splice-instrument.sh`
- **Domain Role:** [[roles/packaging]]
- **Category:** Wine Application Wrapper

## Overview & Purpose
Turnkey launcher script for Splice Instruments running under Wine staging. Applies flock locking, automated SQLite schema patching (Spitfire Error #4), and 48kHz DirectSound initialization.

## Key Interfaces & Exports
- `Spawns Wine prefix with isolated DLL overrides and audio settings`

## Architectural References & Decisions
- [[ADR-007-wine-packaged-applications]]
