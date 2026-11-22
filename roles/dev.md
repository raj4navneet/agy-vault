---
id: ROLE-DEV
type: role_router
role: dev
tags: ["role/dev"]
issue_reference: "http://localhost:3000/agy/nixos-config/issues/34"
description: Standalone software engineering projects located under ~/dev (independent from /etc/nixos).
---
# Dev Role Context & Knowledge Graph

> **Scope:** Independent software engineering repositories and prototypes located outside `/etc/nixos` (e.g. `~/dev/rachna`).

## Functional Domain & Boundary
The `dev` role encapsulates user software development repositories residing in `~/dev`. Unlike host system configuration or agent infrastructure, code in this domain is completely isolated from `/etc/nixos` derivations and system generation rebuilds.

## Projects
- **Rachna:** High-performance ShaderToy & node compositor DAG with 32-bit floating-point rendering pipeline in Rust & Svelte 5 (`~/dev/rachna` & `~/agy-workspaces/ticket-29/rachna`).
- **Dharak:** Universal Git-backed asset librarian vault, iTunes 11 chameleon album grid, and Pixar Tractor DQL query engine (`~/agy-workspaces/dharak`).

## Architectural Decision Records (ADRs) & Engineering Codices
- [[ADR-008-rachna-shadertoy-compositor]] — Rachna: Multi-Pass ShaderToy Compositor DAG & Pipeline
- [[technical/rachna-codex]] — Rachna & Ecosystem Engineering Codex: Ticket #29 Closure & Architectural DNA

## Key File Proxies
- [[rachna]] — High-performance ShaderToy visual compositor DAG & 32-bit float pipeline in Rust.
- [[dharak]] — Git-backed asset librarian and iTunes 11 / Tractor DQL vault.

## Ticket Chronicle Index
- [#27: Phase 0 Headless ShaderToy Compositor CLI Prototype](http://127.0.0.1:3000/agy/nixos-config/issues/27)
- [#28: Phase 1 JSON Recipe Schema, In-Memory DAG & 32-Bit Float Pipeline](http://127.0.0.1:3000/agy/nixos-config/issues/28)
- [#29: Phase 2 Interactive Web GUI, Live WebSocket Server, ShaderToy Importer & Wildcards](http://127.0.0.1:3000/agy/nixos-config/issues/29) · [[tickets/ISSUE-29]]
- [#49: docs(rachna): Knowledge Base Ticket #29 Closure Debrief & Ecosystem Codex](http://127.0.0.1:3000/agy/nixos-config/issues/49)
- [#50: feat(dharak): Universal Git-Backed Asset Librarian, iTunes 11 Album Grid & Pixar Tractor DQL Engine](http://127.0.0.1:3000/agy/nixos-config/issues/50)
- [#51: feat(rachna): Standard Compositing Node Library & Dharak Git-Hash Instancing](http://127.0.0.1:3000/agy/nixos-config/issues/51)
- [#52: feat(rachna): Phase 4 Unified Temporal Transport, Parameter Animation Curves, Video Sequences & Lua/Audio Engine](http://127.0.0.1:3000/agy/nixos-config/issues/52)
