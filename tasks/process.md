---
type: process
role: orchestrator
tags: ["role/orchestrator", "dmb/ram", "tasks/process"]
updated: 2026-10-27
description: "Lifecycle protocol for RAM layer: managing tasks/work/ scratchpads and tasks/log/ archives."
---
# RAM Layer Task Lifecycle & Multi-Writer Protocol

> **Purpose:** Prevents merge conflicts between concurrent human and autonomous agent writers by replacing shared append-only log files with dedicated file-per-task scratchpads and immutable completed logs.

## 1. Directory Structure

```text
.vault/tasks/
├── process.md             # This protocol file
├── work/                  # In-flight scratchpads (one per active ticket/task)
│   └── ISSUE-<ID>-<slug>.md
└── log/                   # Completed task logs (one per resolved ticket)
    └── YYYY-MM-DD-ISSUE-<ID>.md
```

## 2. In-Flight Work Item Lifecycle (`tasks/work/`)

1. **Task Initialization (Pre-Flight):**
   - At the start of a ticket, `./scripts/vault-sync.sh pull <ID>` creates or updates `tasks/work/ISSUE-<ID>-<slug>.md`.
   - The file captures:
     - Active ticket ID and Forgejo URL
     - Goal and acceptance criteria
     - In-flight execution log (steps taken, compiler checks, approvals)
     - Open blockers or decision points

2. **In-Flight Maintenance:**
   - As an agent or developer works, all interim notes, test results, and command findings are logged into this single isolated file.
   - `.vault/active-context.md` links directly to the current file in `tasks/work/`.

## 3. Task Completion & Archival (`tasks/log/`)

1. **Resolution & Push (Post-Flight):**
   - When the task is resolved, `./scripts/vault-sync.sh push <ID>`:
     - Extracts the `## Resolution Summary` from the active work note.
     - Posts the resolution comment to the Forgejo ticket.
     - Moves `tasks/work/ISSUE-<ID>-<slug>.md` to `tasks/log/YYYY-MM-DD-ISSUE-<ID>.md`.
     - Updates `active-context.md` to indicate idle/ready state.

2. **Immutability:**
   - Files in `tasks/log/` are read-only historical records.
   - Future tickets reference historical logs via direct links without modifying existing log files.
