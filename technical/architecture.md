---
id: TECHNICAL-ARCHITECTURE
type: knowledge
role: nix-config
updated: 2026-10-27
tags: ["dmb/knowledge", "technical/architecture", "role/nix-config"]
description: "Core architectural baselines: Clean Architecture, Flask modularity, Redis naming, and DMB pattern."
---
# System Architecture & Design Patterns

> **Purpose**: Core architectural baselines: Clean Architecture, Flask modularity, Redis naming, and DMB pattern.
> **When to use**: Review before creating new modules, refactoring subsystem boundaries, or designing abstractions.

---

## 1. Clean Architecture (Strict Layer Boundaries)

Directories maintain strict separation of concerns:
- **`system/`**: Host-level NixOS modules (kernel, hardware drivers, system daemons, core networking).
- **`home/`**: User-level Home Manager modules (desktop styling, shell, user packages, IDEs).
- **`config/`**: Raw, un-interpolated configuration assets (`hyprland.lua`, `starship.toml`).
- **`scripts/`**: Shell automation, agent tooling, and maintenance scripts.
- **`docs/`**: User guides, setup manuals, and architecture references.
- **Root Entrypoints**: Root shims (`configuration.nix`, `home-manager.nix`) must remain minimal delegation shims (< 25 lines) pointing directly into `system/` and `home/`.

---

## 2. pallets/flask (Fierce Modularity & Decoupled Composition)

- Emulate Flask's blueprint composition pattern.
- All subdomain modules are self-contained and composed explicitly at boundaries (`system/default.nix` for host modules; `home/default.nix` for user modules).
- Zero circular dependencies. Every dependency flows inward toward system composition.

---

## 3. redis/redis (Descriptive Naming Standard)

- Variables, functions, scripts, and module attributes must describe exactly what they do without ambiguity.
- Arbitrary abbreviations are strictly prohibited (`calculate_render_bounds` over `calc_bnds`; `rebuildContainerScript` over `rb_scr`).
- Boolean toggles must sound like questions (`is_active`, `has_children`, `enable_gui`).
- Functions and scripts follow explicit verb-noun naming (`restore_forgejo_database`, `agy-nixos-claim`).

---

## 4. Directed Memory Bank (DMB Substrate)

- **Manifest Runtime Routing:** `INDEX.md` acts as the inventory and relevance matrix, directing agents on exact reading orders by intent.
- **Knowledge vs. RAM Segregation:** Slow-changing system architecture (`project/`, `technical/`, `decisions/`, `proxies/`) is segregated from fast-changing in-flight task memory (`tasks/work/`, `tasks/log/`).
- **Multi-Writer Safety:** File-per-task model prevents concurrent agent merge conflicts.

---

## Cross-References
- Root Manifest: [[INDEX]]
- System Brief: [[project/brief]]
- System Domain: [[project/domain]]
- Technology Stack: [[technical/stack]]
- Role Routers: [[roles/nix-config]], [[roles/orchestrator]], [[roles/packaging]], [[roles/dev]]
