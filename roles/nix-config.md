---
id: ROLE-NIX-CONFIG
type: role_router
role: nix-config
tags: ["role/nix-config"]
issue_reference: "http://localhost:3000/agy/nixos-config/issues/34"
description: Declarative NixOS system configuration, Home Manager modules, hardware drivers, desktop styling, and code purity.
---
# Nix-Config Role Context & Knowledge Graph

> **Scope:** Declarative host-level and user-level configurations in `/etc/nixos` adhering to Clean Architecture and Redis/Go naming standards.

## Functional Domain & Boundary
The `nix-config` role governs the declarative definition of the NixOS operating system, hardware interfaces, Hyprland desktop environment, user dotfiles, and system packages.

## Architectural Decision Records (ADRs)
- [[ADR-002-clean-architecture-and-purity]] — Clean Architecture, Layer Boundaries & Code Purity Constraints

## Core Repository Modules
- `system/`: Host NixOS modules (drivers, kernel, daemons, core networking).
- `home/`: User Home Manager modules (desktop styling, shell, user packages, IDEs).
- `config/`: Raw, un-interpolated configuration assets (`hyprland.lua`, `starship.toml`).
- `scripts/`: Shell automation and system maintenance tools.
- `docs/`: User guides, installation workflows, and architecture references.

## Key File Proxies
- [[configuration.nix]] — Minimal root system entrypoint delegating to `system/default.nix`.
- [[home-manager.nix]] — Minimal root user entrypoint delegating to `home/default.nix`.
- [[flake.nix]] — Nix Flake root specification declaring inputs and outputs.
- [[default.nix]] — Host-level module composer (Flask blueprint style) in `system/default.nix`.
- [[nix-rebuild.sh]] — System build wrapper with timestamped logging to `/etc/nixos/logs/`.

## Ticket Chronicle Index
- [#8: Restructure repository for human readability and clean architecture](http://127.0.0.1:3000/agy/nixos-config/issues/8)
- [#9: Formalize repository architecture, naming, and purity rules](http://127.0.0.1:3000/agy/nixos-config/issues/9)
- [#10: Audit and eliminate non-declarative configs in ~/*](http://127.0.0.1:3000/agy/nixos-config/issues/10)
- [#14: Add Obsidian package to NixOS configuration](http://127.0.0.1:3000/agy/nixos-config/issues/14)
- [#15: Enable fuzzy search and tab autocomplete in terminal](http://127.0.0.1:3000/agy/nixos-config/issues/15)
- [#19: Download Krita and nix-rebuild](http://127.0.0.1:3000/agy/nixos-config/issues/19)
- [#22: Rename ~/Dev to ~/dev](http://127.0.0.1:3000/agy/nixos-config/issues/22)
