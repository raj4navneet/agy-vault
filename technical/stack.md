---
id: TECHNICAL-STACK
type: knowledge
role: nix-config
updated: 2026-10-27
tags: ["dmb/knowledge", "technical/stack", "role/nix-config"]
description: "Complete inventory of technologies, versions, core services, critical warnings, and key design decisions."
---
# Technology Stack Quick Reference

> **Purpose**: Complete inventory of technologies, versions, core services, critical warnings, and key design decisions.
> **When to use**: Starting development, adding dependencies, troubleshooting services, or debugging runtime environments.

---

## Core Technologies

### 1. Operating System & Package Management
- **OS**: NixOS (x86_64-linux), Flakes-based configuration (`/etc/nixos/flake.nix#nixy`).
- **Channel / Upstream**: `nixpkgs-unstable` pinned via flake lockfile.
- **Kernel**: Linux 6.12+ stock kernel with Musnix real-time limits, RTKit, and low-latency preemption (ensuring 100% binary cache hits for NVIDIA drivers).
- **Service Management**: Systemd (custom daemons for orchestrator, Forgejo, and watcher pipelines).

### 2. Desktop Environment & Display
- **Compositor**: Hyprland (Wayland), configured via raw assets in `/etc/nixos/config/hyprland.lua`.
- **Status Bar & Launcher**: Waybar + Wofi / Ulauncher.
- **Terminal Emulator**: Foot / Kitty terminal.
- **Headless Test Compositor**: Cage (`cage -- <command>`), used by `agy-capture.sh` for non-interactive visual verification.

### 3. IssueOps Automation & Agent Harness
- **Harness Language**: Python 3.11+, Bash 5.3.
- **Daemon Framework**: FastAPI + Uvicorn (`orchestrator.py` listening on `127.0.0.1:8081`).
- **Process Isolation**: Bubblewrap (`bwrap`), namespaces for filesystem isolation (`scripts/agy-sandbox.sh`).
- **Session Multiplexer**: tmux (isolated sessions `agy-ticket-<ID>`).
- **Terminal Streaming**: ttyd (`ttyd -p 7714 -i tailscale0 tmux attach-session -t agy-ticket-<ID>`), Tailscale-only access.

### 4. Ticketing, VCS & Synchronization
- **Git Forge**: Forgejo v10 (local instance listening on `http://127.0.0.1:3000`).
- **Database**: SQLite3 (`/var/lib/forgejo/data/forgejo.db`).
- **State Snapshot**: `/etc/nixos/forgejo-state/forgejo-data.sql` synced via `scripts/forgejo-sync.sh`.
- **CLI Client**: `tea` CLI (configured under `navigator` and `agy` credentials).
- **Ticketing Automation**: `scripts/tea-ticket.sh` (handles issue creation, stopwatch tracking, and user request audit logging).

### 5. Mobile Approval & Notification Bridge
- **Notification Broker**: ntfy.sh (`ntfy.sh/agy-approvals` and `ntfy.sh/agy-alerts`).
- **Approval Gate**: `scripts/agy-ask.sh` (runs `nixos-rebuild dry-build` before prompting phone).
- **Media Dispatcher**: `scripts/agy-attach.sh` (uploads visual proof images to Forgejo and emits mobile previews).

### 6. Creative Audio, Obsidian & Windows Packaging
- **Audio Server**: PipeWire + WirePlumber with low-latency audio buffer configurations.
- **Windows Translation**: Wine-GE / Proton + yabridge (Windows VST/VST3 bridging).
- **State Harvester**: `scripts/harvest-partial-declarative.sh` and `home/programs/partial-declarative.nix` (seeds declarative baseline configs while preserving runtime mutability).
- **Knowledge Vault**: Obsidian (`~/Documents/obsidian/agy_vault` symlinked to `/etc/nixos/.vault`).

---

## Key Design Decisions & Trade-offs

| Decision | Rationale | Trade-off |
| :--- | :--- | :--- |
| **Nix Flakes (`flake.nix`)** | 100% reproducible system builds and pinned lockfile dependencies. | Stricter evaluation; untracked files in git are ignored by Nix. |
| **Bubblewrap (`bwrap`) Sandboxing** | Lightweight namespace isolation for agents without Docker daemon overhead. | Requires explicit bind mounts for `/nix/store` and workspace directories. |
| **Local Forgejo over Cloud GitHub** | Full offline autonomy; zero rate limits; instant webhook delivery to localhost. | Requires declarative backup snapshots (`forgejo-sync`) to protect data. |
| **Tailscale-Bound `ttyd` Streaming** | Secure live mobile terminal inspection from phone without exposing public ports. | Requires Tailscale connection on the client phone. |
| **Directed Memory Bank (`.vault/`)** | Portable markdown context; works with any agent; sub-10ms ripgrep backlink queries. | Requires disciplined doc maintenance and strict length budgets. |

---

## Critical Warnings & Guardrails

> [!WARNING]
> **No Direct Commits to Main**: The live `/etc/nixos` repository is locked against direct commits. Always claim the lock using `agy-nixos-claim <ID>` and commit strictly on branch `ticket-<ID>`.

> [!IMPORTANT]
> **Compiler Gate Before Phone Prompting**: Rebuild requests must always be initiated via `scripts/agy-ask.sh <ID> "<command>"`. `agy-ask` runs a pre-flight dry-build compiler check before sending approval requests to `@navigator`'s phone.

> [!CAUTION]
> **Active Time Tracking Only**: Stopwatches must never run during pauses, human reviews, or overnight idle spans. Always run `tea-ticket stop-timer <ID>` when yielding control.

---

## Cross-References
- Root Manifest: [[INDEX]]
- System Brief: [[project/brief]]
- System Architecture: [[technical/architecture]]
- Role Routers: [[roles/nix-config]], [[roles/orchestrator]], [[roles/packaging]], [[roles/dev]]
