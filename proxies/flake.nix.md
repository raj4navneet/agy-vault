---
id: PROXY-flake.nix
type: file_proxy
file_path: "/etc/nixos/flake.nix"
role: nix-config
tags: ["file_proxy", "role/nix-config"]
role_router: "[[roles/nix-config]]"
last_updated: "2026-10-27"
---
# File Proxy: `flake.nix`

## Metadata
- **Path on Disk:** `/etc/nixos/flake.nix`
- **Domain Role:** [[roles/nix-config]]
- **Category:** Flake Root Entrypoint

## Overview & Purpose
Nix Flake entrypoint defining dependencies (nixpkgs, home-manager, hyprland) and assembling the nixy system configuration derivation.

## Key Interfaces & Exports
- `nixosConfigurations.nixy: Main system output derivation`

## Architectural References & Decisions
- [[ADR-002-clean-architecture-and-purity]]
