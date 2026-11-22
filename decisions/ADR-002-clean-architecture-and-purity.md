---
id: ADR-002
type: decision
role: nix-config
tags: ["role/nix-config"]
status: accepted
role_router: "[[roles/nix-config]]"
related_tickets: ["[#8](http://127.0.0.1:3000/agy/nixos-config/issues/8)", "[#9](http://127.0.0.1:3000/agy/nixos-config/issues/9)"]
related_files: ["[[configuration.nix]]", "[[home-manager.nix]]", "[[AGENTS.md]]"]
---
# ADR-002: Clean Architecture, Layer Boundaries & Code Purity Constraints

**Role:** [[roles/nix-config]]

## Context
System configuration previously had monolithic configuration files, blended host/home boundaries, and arbitrary abbreviations.

## Decision
1. Decompose system into strict Clean Architecture layers:
   - `system/`: Host NixOS modules (drivers, kernel, daemons).
   - `home/`: User Home Manager modules (desktop styling, shell, user apps).
   - `config/`: Un-interpolated assets.
   - `scripts/`: Shell automation and maintenance tools.
   - `docs/`: User guides and architecture references.
2. Adhere to four baselines:
   - Redis descriptive naming (zero arbitrary abbreviations).
   - Flask blueprint modularity (zero circular dependencies).
   - Go standard library boring, explicit readability over cleverness.
   - Strict 200-line file purity constraint and zero zombie code.
