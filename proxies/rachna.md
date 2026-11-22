---
id: PROXY-rachna
type: file_proxy
file_path: "/home/navigator/dev/rachna"
role: dev
tags: ["file_proxy", "role/dev"]
role_router: "[[roles/dev]]"
last_updated: "2026-10-27"
---
# File Proxy: `rachna`

## Metadata
- **Path on Disk:** `/home/navigator/dev/rachna`
- **Domain Role:** [[roles/dev]]
- **Category:** Independent Dev Project

## Overview & Purpose
High-performance ShaderToy visual compositor DAG and 32-bit floating-point rendering pipeline written in Rust with wgpu and naga.

## Key Interfaces & Exports
- `Cargo project: ~/dev/rachna`
- `CLI binary: rachna --shader <s> -o <out.png>`

## Architectural References & Decisions
- [[ADR-008-rachna-shadertoy-compositor]]
