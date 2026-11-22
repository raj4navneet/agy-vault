---
id: INDEX
type: index
architecture: "Directed Memory Bank (DMB)"
standard: "pmikutel/directed-memory-bank"
updated: 2026-10-27
roles: ["nix-config", "orchestrator", "packaging", "dev"]
total_roles: 4
issue_reference: "http://localhost:3000/agy/nixos-config/issues/34"
---
# Directed Memory Bank (DMB) — Context Router & Graph Index

> **Agent Instruction:** Read this top-level manifest to identify your operational intent. Use the **Operation-Scoped Context Discovery Matrix** below to load strictly the minimal relevant knowledge files in the prescribed reading order. Navigate to the corresponding **Domain Role Router** for localized ADRs, tracebacks, and file proxies. Backlinks are strictly segregated by role to avoid cross-domain graph entanglement and are queried locally in <10ms via `rg "\[\[TargetName\]\]" .vault/`.

---

## 1. Two-Layer Architecture Overview

| Layer | Directories | Purpose & Rate of Change |
| :--- | :--- | :--- |
| **Knowledge Layer** | `project/`, `technical/`, `decisions/`, `roles/`, `proxies/`, `tracebacks/` | Durable system truth, architectural baselines, 1-hop file proxies, and historical tracebacks. Slow to medium change. |
| **RAM Layer** | `tasks/work/`, `tasks/log/`, `active-context.md` | In-flight ticket scratchpads, active execution focus, and completed ticket chronicles. Fast-changing, multi-writer safe. |

---

## 2. Operation-Scoped Context Discovery Matrix

Load only what is relevant to your current operational task, following the reading sequence from left to right:

| Operation Intent | 1. Primary Core Files | 2. Domain Role Router | 3. Domain Proxies, ADRs & Tracebacks *(via Role Router)* |
| :--- | :--- | :--- | :--- |
| **SYSTEM & HOME DEV**<br>*(NixOS host modules, Home Manager, desktop, shell)* | 1. [[project/brief]]<br>2. [[technical/stack]]<br>3. [[technical/architecture]] | [[roles/nix-config]] | **Proxies**: `configuration.nix`, `home-manager.nix`, `flake.nix`, `default.nix`, `nix-rebuild.sh`<br>**ADRs**: `ADR-002-clean-architecture-and-purity` |
| **ISSUEOPS & AUTOMATION**<br>*(Orchestrator, Bubblewrap, ttyd, FIFO lock, mobile gate)* | 1. [[project/brief]]<br>2. [[technical/stack]]<br>3. [[technical/architecture]] | [[roles/orchestrator]] | **Proxies**: `orchestrator.py`, `agy-sandbox.sh`, `agy-nixos-claim.sh`, `agy-ask.sh`, `tea-ticket.sh`, `vault-sync.sh`<br>**ADRs**: `ADR-001`, `ADR-003`, `ADR-005`, `ADR-006`, `ADR-009` |
| **PACKAGING & AUDIO**<br>*(Wine-GE, yabridge, Splice, declarative state harvester)* | 1. [[project/brief]]<br>2. [[technical/stack]] | [[roles/packaging]] | **Proxies**: `harvest-partial-declarative.sh`, `splice-instrument.sh`, `registry-patches.reg`<br>**ADRs**: `ADR-004`, `ADR-007` · **Tracebacks**: `TB-004`, `TB-006` |
| **STANDALONE SOFTWARE**<br>*(Independent projects in `~/dev`, compositors, tools)* | 1. [[project/brief]] | [[roles/dev]] | **Proxy**: `rachna`<br>**ADR**: `ADR-008-rachna-shadertoy-compositor` |
| **INCIDENTS & DEBUGGING**<br>*(Compiler errors, crashes, sudo/permission faults)* | 1. [[project/brief]]<br>2. [[technical/stack]]<br>3. [[technical/architecture]] | Target Role Router | **Tracebacks**: Query `rg "\[\[TargetFile\]\]" .vault/tracebacks/`<br>Template: `TB-000-template` · Notable: `TB-001`..`TB-006` |
| **VAULT MAINTENANCE**<br>*(Refactoring notes, adding ADRs/proxies, syncing tickets)* | 1. [[project/doc-guide]]<br>2. [[tasks/process]] | [[roles/orchestrator]] | **Proxy**: `vault-sync.sh`, `AGENTS.md`, `GEMINI.md`<br>**ADRs**: `ADR-001-hybrid-memory`, `ADR-009-directed-memory-bank` |

---

## 3. Core Knowledge Layer (`project/` & `technical/`)

- [[project/brief]] — 30-second system understanding, headline goals, and boundaries. **Load first on every session.**
- [[project/domain]] — Domain entities, ticket lifecycles, time tracking invariants, and operational rules.
- [[project/doc-guide]] — Vault note hygiene, style conventions, length budgets, and frontmatter schema.
- [[technical/stack]] — Authoritative inventory of technologies, versions, services, trade-offs, and warnings.
- [[technical/architecture]] — 4-tier Clean Architecture design, IssueOps execution pipeline, and DMB substrate layout.

---

## 4. Active State & RAM Layer (`tasks/`)

- [[active-context]] — Current in-flight ticket pointer, active branch, and directed retrieval commands.
- [[tasks/process]] — RAM layer lifecycle, multi-writer scratchpad conventions, and knowledge promotion protocol.
- **`tasks/work/`** — Isolated working scratchpads for in-flight tickets (`tasks/work/ticket-<ID>-<slug>.md`).
- **`tasks/log/`** — Immutable permanent chronicles of completed units of work (`tasks/log/ticket-<ID>-<slug>.md`).

---

## 5. Functional Domain Role Routers (`roles/`)

Each Role Router owns the direct `[[...]]` wikilinks to its domain-specific **ADRs** (`decisions/`), **Incident Tracebacks** (`tracebacks/`), and **File Proxies** (`proxies/`), keeping the Obsidian knowledge graph cleanly partitioned by functional role:

- [[roles/nix-config]] — **NixOS System Configuration**: Host modules, Home Manager, hardware drivers, desktop styling, and code purity constraints.
- [[roles/orchestrator]] — **Orchestrator & Agent Ops**: Autonomous IssueOps, Bubblewrap sandboxing, FIFO lock queue, mobile control bridge, and audit protocol.
- [[roles/packaging]] — **Wine Packaging & State**: Declarative Nix packaging for Windows audio/graphics apps (Splice, Affinity) and partial-declarative config harvester.
- [[roles/dev]] — **Independent Dev Projects**: Standalone software engineering repositories and prototypes residing in `~/dev` (e.g. Rachna visual compositor).

---

## 6. Sub-10ms 1-Hop Local Graph Navigation

Before editing any file `module.nix` or `script.sh`, execute:
```bash
rg "\[\[module\.nix\]\]" .vault/
```
This surfaces connected file proxies, ADRs, past incident tracebacks, and role routers in under 10 milliseconds.
