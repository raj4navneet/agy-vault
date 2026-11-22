---
id: ADR-008
type: decision
role: dev
tags: ["role/dev"]
status: accepted
role_router: "[[roles/dev]]"
related_tickets: ["[#27](http://127.0.0.1:3000/agy/nixos-config/issues/27)", "[#28](http://127.0.0.1:3000/agy/nixos-config/issues/28)", "[#29](http://127.0.0.1:3000/agy/nixos-config/issues/29)"]
related_files: ["[[rachna]]"]
---
# ADR-008: Rachna: Multi-Pass ShaderToy Compositor DAG & Pipeline

**Role:** [[roles/dev]]

## Context
Need an extensible visual composition pipeline to evaluate ShaderToy GLSL shaders headlessly and interactively.

## Decision
1. Phase 0: CLI headless compositor rendering multipass fragment shaders to PNG.
2. Phase 1: Declarative JSON recipe schema with in-memory directed acyclic graph (DAG) and 32-bit floating point image buffers.
3. Phase 2: Interactive Web GUI with WebSocket server for hot-reloading shaders and parameter tweaking.
