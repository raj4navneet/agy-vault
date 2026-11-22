---
id: ROLE-PACKAGING
type: role_router
role: packaging
tags: ["role/packaging"]
issue_reference: "http://localhost:3000/agy/nixos-config/issues/34"
description: Wine application packaging (Splice, Affinity), SQLite runtime patches, and partial-declarative config harvesting.
---
# Packaging Role Context & Knowledge Graph

> **Scope:** Standalone flakes and declarative packaging wrappers for Wine-based creative applications.

## Functional Domain & Boundary
The `packaging` role handles standalone flake packaging, runtime library isolation, and partial-declarative state synchronization for complex proprietary Windows desktop applications running under Wine staging.

## Architectural Decision Records (ADRs)
- [[ADR-004-partial-declarative-harvesting]] — Partial-Declarative Config Harvester for GUI & Wine State
- [[ADR-007-wine-packaged-applications]] — Declarative Nix Packaging for Wine Applications (Splice & Affinity)

## Incident Tracebacks & Root Causes
- [[TB-004-spitfire-error-4-sqlite-missing-ir]] — SQLite impulse response database patch for Splice crash
- [[TB-006-splice-audio-buffer-latency-underrun]] — Low-latency WASAPI buffer and 48kHz audio tuning

## Key File Proxies
- [[harvest-partial-declarative.sh]] — Harvester for mutable Wine registry and GUI configs into `/etc/nixos`.
- [[splice-instrument.sh]] — Turnkey Wine launcher script with Spitfire Error #4 SQLite patching and flock.
- [[splice-instrument.settings]] — Sanitized partial-declarative baseline for Splice preferences.
- [[splice-user.reg]] — Sanitized partial-declarative Wine registry hive baseline.
- [[registry-patches.reg]] — Audio buffer overrides and low-latency registry patches.

## Ticket Chronicle Index
- [#11: Architect Partial-Declarative Config Harvester for GUI Apps](http://127.0.0.1:3000/agy/nixos-config/issues/11)
- [#16: Setup Affinity on NixOS](http://127.0.0.1:3000/agy/nixos-config/issues/16)
- [#24: Fix Splice Instruments blank white screen and crash](http://127.0.0.1:3000/agy/nixos-config/issues/24)
- [#25: Turnkey self-extracting SpliceINSTRUMENT-nix package](http://127.0.0.1:3000/agy/nixos-config/issues/25)
- [#26: Snapshot Wine working prefix and test declarative rebuild](http://127.0.0.1:3000/agy/nixos-config/issues/26)
- [#30: Compress zip older manual Splice instrument](http://127.0.0.1:3000/agy/nixos-config/issues/30)
- [#31: Splice Instrument massive lag and audio underrun](http://127.0.0.1:3000/agy/nixos-config/issues/31)
- [#32: Reverse engineer SpliceInstrument using REA](http://127.0.0.1:3000/agy/nixos-config/issues/32)
