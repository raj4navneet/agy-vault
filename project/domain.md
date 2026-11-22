---
id: PROJECT-DOMAIN
type: knowledge
role: orchestrator
updated: 2026-10-27
tags: ["dmb/knowledge", "project/domain", "role/orchestrator"]
description: "Domain models, entity definitions, functional roles, operational lifecycles, and core business rules."
---
# System Domain & Operational Models

> **Purpose**: Domain models, entity definitions, functional role boundaries, operational lifecycles, and core business rules.
> **When to use**: Consult during ticket intake, requirement formulation, or workflow updates.

---

## 1. Functional Roles & Domain Boundaries

The system segregates all engineering domains into 4 isolated roles:

| Role | Domain Scope | Primary Paths | Role Router |
| :--- | :--- | :--- | :--- |
| **`nix-config`** | Host NixOS modules, kernel, hardware drivers, Home Manager, desktop styling | `/etc/nixos/system/`, `/etc/nixos/home/`, `flake.nix` | [[roles/nix-config]] |
| **`orchestrator`** | Autonomous agent ops, Bubblewrap sandbox, lock queue, mobile bridge, vault sync | `/etc/nixos/orchestrator/`, `/etc/nixos/scripts/agy-*` | [[roles/orchestrator]] |
| **`packaging`** | Wine applications (Splice, Affinity), registry patches, state harvester | `home/programs/partial-declarative.nix`, `harvest-partial-declarative.sh` | [[roles/packaging]] |
| **`dev`** | Independent software repositories outside `/etc/nixos` | `/home/navigator/dev/` (e.g. Rachna visual compositor) | [[roles/dev]] |

---

## 2. Domain Entities

| Entity | Location / Store | Description |
| :--- | :--- | :--- |
| **Ticket / Issue** | Forgejo (`agy/nixos-config`) | Canonical record of work, discussion history, user requests, and resolution chronicles. |
| **Active Stopwatch** | Forgejo SQLite (`tea api user/stopwatches`) | Real-time stopwatch tracking active execution. Must never record idle human wait time. |
| **Tracked Time** | Forgejo SQLite (`tea times`) | Permanent log of active engineering duration attached to an issue. |
| **NixOS Concurrency Lock** | Orchestrator memory / FIFO queue (`agy-nixos-claim`) | Mutual exclusion lock ensuring only one agent writes to `/etc/nixos` at a time. |
| **Sandbox Workspace** | `~/agy-workspaces/ticket-<ID>` | Ephemeral Bubblewrap container workspace where agents explore, stage, and test code. |
| **Mobile Approval Gate** | `scripts/agy-ask.sh` + ntfy.sh | Two-phase verification gate: automated compiler dry-build followed by mobile phone sign-off. |
| **Visual Proof Artifact** | `~/agy-workspaces/ticket-<ID>/proof.png` | Screenshot rendered in headless `cage` compositor or live Hyprland via `agy-capture.sh`. |
| **File Proxy** | `.vault/proxies/<file>.md` | 1-hop Obsidian markdown node mirroring a system file for instant architectural summary & backlink queries. |
| **Incident Traceback** | `.vault/tracebacks/TB-<num>-<slug>.md` | Structured post-mortem documenting root causes, error traces, and safeguards. |

---

## 3. Operational Lifecycles

### Ticket Execution Lifecycle

```
[User Request / Bug Report]
            │
            ▼
┌──────────────────────────┐
│  Phase 1: Ticket Intake  │ ──► tea-ticket create --title ... --request ...
│  (Stopwatch Started)     │ ──► Attach 'in-progress' label
└───────────┬──────────────┘
            │
            ▼
┌──────────────────────────┐
│  Phase 2: NixOS Claim    │ ──► agy-nixos-claim <ID>
│  (FIFO Lock Queue)       │ ──► Check out branch 'ticket-<ID>'
└───────────┬──────────────┘
            │
            ▼
┌──────────────────────────┐
│  Phase 3: Investigation  │ ──► Read .vault/active-context.md & .vault/INDEX.md
│  (Structured Comment)    │ ──► Post plan comment: tea comment <ID> "..."
└───────────┬──────────────┘
            │
            ▼
┌──────────────────────────┐
│  Phase 4: Implementation │ ──► Edit files adhering to Clean Architecture & Redis naming
│  & Verification Gate     │ ──► Pre-flight dry-build check & mobile approval via agy-ask
└───────────┬──────────────┘
            │
            ▼
┌──────────────────────────┐
│  Phase 5: Commit & Proof │ ──► Visual verification via agy-capture & agy-attach
│  (Forgejo Trailer)       │ ──► git commit -m "feat(scope): ... (Closes #<ID>)"
└───────────┬──────────────┘
            │
            ▼
┌──────────────────────────┐
│  Phase 6: Close & Sync   │ ──► tea-ticket stop-timer <ID>
│  (Database Snapshot)     │ ──► Labels: remove 'in-progress', add 'resolved'
│                          │ ──► Close issue & run forgejo-sync
└──────────────────────────┘
```

### Time Tracking Invariants (Active Execution Only)

1. **Active Stopwatch Only During Execution**: Stopwatches must only accumulate time when the agent is actively editing, compiling, or executing commands.
2. **Stop Before Yielding**: Whenever yielding control to the user (asking a question, waiting for phone approval, awaiting review), stop the stopwatch timer (`tea-ticket stop-timer <ID>`).
3. **No Wall-Clock Bloat**: Never allow overnight or multi-hour idle spans. Accidental spikes must be pruned using `tea times delete <ID> <time-id>`.

### Memory Boundary: Control Plane vs. Memory Plane

- **Control Plane (Forgejo)**: Single source of truth for tickets, comments, user prompt audit logs, git branches, and time tracking.
- **Memory Plane (`.vault/`)**: Local markdown knowledge graph optimized for sub-10ms ripgrep queries, Obsidian visual graph traversal, and zero-conflict multi-writer safety.

---

## 4. Core Domain Rules

1. **"No Ticket, No Code"**: Modifying system files, modules, or scripts without an active ticket is strictly prohibited.
2. **"Code Stays Clean; Tickets Hold the Essay"**: System files and `.nix` modules contain only operational code and concise "why" comments. Investigative narratives and debug sub-plots live on Forgejo tickets.
3. **Read-Only `/etc/nixos` Default**: Working trees are read-only by default. Live system modification requires holding the ticket lock on the specific `ticket-<ID>` branch.
4. **Dry-Build Before Human Notification**: Rebuild testing commands must be evaluated by `nixos-rebuild dry-build` before triggering phone notifications.

---

## Cross-References
- Root Manifest: [[INDEX]]
- System Brief: [[project/brief]]
- Documentation Guide: [[project/doc-guide]]
- Technology Stack: [[technical/stack]]
- System Architecture: [[technical/architecture]]
- Role Routers: [[roles/nix-config]], [[roles/orchestrator]], [[roles/packaging]], [[roles/dev]]
