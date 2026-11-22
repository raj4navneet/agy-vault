---
id: PROXY-configuration.nix
type: file_proxy
file_path: "/etc/nixos/configuration.nix"
role: nix-config
tags: ["file_proxy", "role/nix-config"]
role_router: "[[roles/nix-config]]"
last_updated: "2026-10-27"
---
# File Proxy: `configuration.nix`

## Metadata
- **Path on Disk:** `/etc/nixos/configuration.nix`
- **Domain Role:** [[roles/nix-config]]
- **Category:** Root System Delegation Shim

## Overview & Purpose
Minimal (< 25 lines) root system entrypoint delegating all host NixOS module imports directly to system/default.nix in accordance with Clean Architecture.

## Key Interfaces & Exports
- `Imports ./system`
- `Configures system.stateVersion`

## Architectural References & Decisions
- [[ADR-002-clean-architecture-and-purity]]
