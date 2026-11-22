---
title: "Rachna & Ecosystem Engineering Codex: Ticket #29 Closure & Architectural DNA"
date: 2026-11-10
tags:
  - rachna
  - dharak
  - architecture/codex
  - vfx-pipeline
  - rust
  - wgpu
  - svelte5
  - design-philosophy
aliases:
  - Rachna Debrief
  - Navigator Software Philosophy
  - AGY Context Codex
status: milestone-closed
ticket: "#29"
---

# Rachna & Ecosystem Engineering Codex
> **Purpose of this Document:** This note serves both as the definitive closure debrief for **Ticket #29** (Phases 0 through 3B + Katana VFX UX Overhaul) and as a permanent **Obsidian MOC (Map of Content) / Architectural Codex** for future development and AI agents (`agy`). It codifies *what* was built, *how* it works, and *why* specific architectural and ergonomic choices are non-negotiable.

### Connected Knowledge Graph (Obsidian Backlinks)
- **Core Engine:** [[Rachna Engine Architecture]] · [[wgpu Sibling Pipelines]] · [[SipHash DAG Caching]]
- **Asset & Version Control:** [[Dharak Librarian Architecture]] · [[iTunes 11 Expanded Album UI]] · [[Pixar Tractor DQL Filter Engine]] · [[Git Squash-on-Tag Workflow]]
- **Node Libraries:** [[Rachna Standard Compositing Library]] · [[Declarative Shader Params]]
- **Temporal & Audio:** [[Rachna Audio and Timeline Engine]] · [[LuaJIT DSP Runtime]]
- **Design System:** [[Quiet Book Gruvbox Standard]] · [[Houdini Annular Radial Collars]] · [[Katana 3-Column Layout]]

---

## 1. Core Software Design Philosophy (The "Why" for Future AI Agents)

When building or modifying software in this ecosystem (**Rachna**, **Dharak**, or companion pipeline utilities), every architectural decision must align with these foundational principles:

### 1.1 Two Complementary Visual Paradigms: "Quiet Book" DCC & "iTunes 11 + Tractor" Vault
- **For Node & Code Workstations (`Rachna` — Quiet Book Gruvbox):**
  - **No Pure Blacks or Pure Whites:** Never use `#000000` or `#ffffff`. Ground surfaces in warm, paper-like charcoal (`#1d2021`, `#282828`, `#32302f`) and warm cream typography (`#ebdbb2`, `#d5c4a1`, `#fbf1c7`).
  - **Quiet Until Interacted With:** Node chrome (like Houdini radial collars) stays low-contrast at rest, illuminating only on hover or when an active flag is asserted.
- **For Personal Vaults & Asset Curation (`Dharak` — 2012 iTunes 11 Expanded Album Grid + Pixar Tractor Query Engine):**
  - **Monochrome Chrome, Colorful Content:** Keep the surrounding application frame quiet and monochrome so the square **Album Covers** of projects, font collections, wallpapers, and shader libraries provide the color.
  - **Inline Chameleon Expansion:** Clicking an Album splits the grid row in-place and opens a full-width drawer that dynamically samples its background and typography colors from the album's cover art (with the artwork fading into the right-hand bleed and a 2-column numbered tracklist on the left).
  - **Pixar Tractor Boolean Filtering (`DQL`):** Everything in the Vault can be sliced in sub-milliseconds using boolean predicate expressions (`kind=font and (tag=writing or attr.foundry=Klim) and not tag=monospace`) for quick ad-hoc viewing, or saved with one click as a permanent **Smart Album**.

### 1.2 Open, Text-First, Self-Describing Data Formats
- **No Proprietary Binary Lock-In:** Project files (`.rachna.json`) and asset sidecars must be plain text, human-readable, and cleanly diffable by Git.
- **Sparse Instancing over Duplication:** Do not bloat project files by duplicating standard library shader code inside every node instance. Store the **Dharak Git Commit SHA + Sparse Parameter Overrides**, reconstructing the node dynamically on load.
- **Comments as Compiler Directives:** Avoid separate UI boilerplate files. A single comment line in a shader (`// @param point2d center = 0.5, 0.5`) or Lua script (`-- @param float cutoff = 440.0 [20.0, 20000.0]`) is the API—automatically generating uniform buffers, GUI sliders, and interactive viewport gizmos.

### 1.3 Strict Decoupling: Headless Daemon vs. Thin Control Surface
- **Headless-First Execution:** Every tool (`rachna`, `dharak`) compiles to a single native Rust binary that runs headless on CLI/farm nodes without an X11/Wayland display requirement.
- **Web UI as a Pure Controller:** The Svelte 5 frontend is a stateless visual viewport and controller talking over WebSockets/REST. All heavy lifting (DAG sorting, GPU dispatches, Git operations, Tractor DQL evaluation, EXR compression, cover color sampling) lives in Rust.
- **External Tools Never Dictate Internal Architecture:** External tools like **DNEG xSTUDIO** (for 32-bit float HDR monitoring) or `$EDITOR` (`nvim`, `code`, `hx`) plug into the daemon via standard POSIX primitives (`/dev/shm`, UDP, `notify` file watchers).

### 1.4 Code & Engineering Conventions
- **Internal Helper Naming:** Follow the `_<verb>_<noun>` convention for internal methods where applicable.
- **Python Bridge Simplicity:** In Python DCC bridges (Katana, Houdini, Nuke), use built-in standard library modules (`os`, `urllib.request`, `json`, `socket`) instead of `pathlib` or heavy third-party packages.
- **Zero-Panic Live Loops:** Never `.unwrap()` user-supplied shader code, JSON payloads, DQL queries, or Git subprocesses on a server worker thread.

---

## 2. Ticket #29 Closure Summary: From CLI Prototype to 12,826-Line Workstation

| Milestone | Scope Delivered | Key Engineering Breakthrough |
| :--- | :--- | :--- |
| **Phase 0 (#27)** | Headless ShaderToy CLI | Fullscreen triangle via `gl_VertexIndex` (zero vertex buffers) + `naga` GLSL regex polyfill for `sampler2D(iChannelX, iSampler)`. |
| **Phase 1 (#28)** | Generic DAG & 32-Bit Float | Upgraded pipeline to linear `Rgba32Float`, native OpenEXR (`exr`), `daggy` cycle rejection, reverse-DFS dead-branch pruning, and 64-bit SipHash VRAM caching. |
| **Phase 2 (#29)** | Live Server & Web GUI | Axum `/ws` server retaining `GpuContext` in VRAM, autonomous ShaderToy scraper, wildcard globbing (`~/`), and SvelteFlow canvas. |
| **Turns 4–8 (UX)** | Katana + Houdini + Gruvbox | 3-column Katana layout (Viewer \| DAG \| Inspector), Quiet Book Gruvbox theme, top-to-bottom flow, 44px Houdini circular nodes with 4-sector SVG annular radial collars (`[B]`, `[V]`, `[i]`, `[P]`), and ComfyUI/Blender shortcuts (`L` auto-layout, `[Y]` laser scissor cut, wire-drop auto-connect). |
| **Phase 3A** | Gizmos, xSTUDIO & Sub-4ms Eval | Polymorphic `PortData`, `// @param` binding 6 injector, 1:1 DOM-scaled `GizmoOverlay.svelte`, async `/dev/shm` EXR writer for xSTUDIO, `$EDITOR` live watcher, and `FilterType::Sub` fast PNG encoding (~3.8ms GPU eval, ~7.8ms total RTT). |
| **Phase 3B** | Sibling Compute & Feedback | Added `wgpu::ComputePass` (`NodeKind::Compute`, `.wgsl`/`.comp`) alongside Fragment pipeline, dual output (`out_buffer` + `@binding(9)` companion texture), and tick-salted $z^{-1}$ temporal ping-pong buffers. |
| **VFX Overhaul** | Chunks 1–10 Polish | Upstream dynamic resolution inheritance (`null` dims), artist VFX naming (*Procedural Generator*, *Shader Filter*, *Image Read*, *Render Output*), strict port gating, `F10` offline EXR export, and `HistoryDelta` diff compression. |

---

## 3. Final Ticket #29 Verification Metrics
- **Codebase Footprint:** `12,826 lines` (`5,925` lines Rust across 11 modules + `6,901` lines Svelte 5/CSS across 12 components).
- **Automated Test Suite:** `31 / 31 passing` in `1.33s` (`cargo test -- --test-threads=1`).
- **Frontend Production Build:** `402 modules` transformed in `1.41s` with `0 errors, 0 warnings`.
- **Interactive Frame Latency:** `2.35 ms – 3.85 ms` GPU cook; `~7.8 ms` (>120 FPS) full WebSocket round-trip.