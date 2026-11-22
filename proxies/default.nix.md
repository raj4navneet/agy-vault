---
id: PROXY-default.nix
type: file_proxy
file_path: "/etc/nixos/system/default.nix"
role: nix-config
tags: ["file_proxy", "role/nix-config"]
role_router: "[[roles/nix-config]]"
last_updated: "2026-10-27"
---
# File Proxy: `default.nix`

## Metadata
- **Path on Disk:** `/etc/nixos/system/default.nix`
- **Domain Role:** [[roles/nix-config]]
- **Category:** System Composition Blueprint

## Overview & Purpose
Flask-blueprint-style module aggregator for host-level NixOS configurations. Composes kernel, hardware, desktop environment, and daemon submodules.

## Key Interfaces & Exports
- `Imports system/core, system/hardware, system/services, system/desktop`

## Architectural References & Decisions
- [[ADR-002-clean-architecture-and-purity]]
