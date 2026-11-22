---
id: PROXY-nix-rebuild.sh
type: file_proxy
file_path: "/etc/nixos/scripts/nix-rebuild.sh"
role: nix-config
tags: ["file_proxy", "role/nix-config"]
role_router: "[[roles/nix-config]]"
last_updated: "2026-10-27"
---
# File Proxy: `nix-rebuild.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/nix-rebuild.sh`
- **Domain Role:** [[roles/nix-config]]
- **Category:** System Build Wrapper

## Overview & Purpose
Wrapper script for nixos-rebuild switch --flake /etc/nixos#nixy with automatic timestamped logging into /etc/nixos/logs/rebuild-YYYY-MM-DD-HHMMSS.log.

## Key Interfaces & Exports
- `Executes sudo nixos-rebuild switch`
- `Redirects stdout and stderr to /etc/nixos/logs/`

## Architectural References & Decisions
- [[ADR-002-clean-architecture-and-purity]]
