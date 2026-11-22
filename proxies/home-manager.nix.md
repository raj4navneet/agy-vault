---
id: PROXY-home-manager.nix
type: file_proxy
file_path: "/etc/nixos/home-manager.nix"
role: nix-config
tags: ["file_proxy", "role/nix-config"]
role_router: "[[roles/nix-config]]"
last_updated: "2026-10-27"
---
# File Proxy: `home-manager.nix`

## Metadata
- **Path on Disk:** `/etc/nixos/home-manager.nix`
- **Domain Role:** [[roles/nix-config]]
- **Category:** Root User Delegation Shim

## Overview & Purpose
Minimal (< 25 lines) root user entrypoint delegating all Home Manager configuration directly to home/default.nix in accordance with Clean Architecture.

## Key Interfaces & Exports
- `Imports ./home`
- `Configures home-manager user baseline`

## Architectural References & Decisions
- [[ADR-002-clean-architecture-and-purity]]
