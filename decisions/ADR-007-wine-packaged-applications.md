---
id: ADR-007
type: decision
role: packaging
tags: ["role/packaging"]
status: accepted
role_router: "[[roles/packaging]]"
related_tickets: ["[#16](http://127.0.0.1:3000/agy/nixos-config/issues/16)", "[#24](http://127.0.0.1:3000/agy/nixos-config/issues/24)", "[#25](http://127.0.0.1:3000/agy/nixos-config/issues/25)", "[#26](http://127.0.0.1:3000/agy/nixos-config/issues/26)", "[#30](http://127.0.0.1:3000/agy/nixos-config/issues/30)", "[#31](http://127.0.0.1:3000/agy/nixos-config/issues/31)", "[#32](http://127.0.0.1:3000/agy/nixos-config/issues/32)"]
related_files: ["[[splice-instrument.sh]]", "[[flake.nix]]", "[[registry-patches.reg]]"]
---
# ADR-007: Declarative Nix Packaging for Wine Applications (Splice & Affinity)

**Role:** [[roles/packaging]]

## Context
Proprietary Windows audio and creative applications require exact runtime DLLs, Wine staging compatibility, and SQLite database patches.

## Decision
1. Package complex Wine applications using standalone flakes (`spliceInstrument-nix`, `affinity-nix`).
2. Provide turnkey launcher script with flock concurrency protection, automatic SQLite schema patching (e.g. Spitfire Error #4), and DirectSound 48kHz pre-seeding.
3. Apply registry optimizations for light theme, WebView2 runtime isolation, and low-latency audio streaming.
