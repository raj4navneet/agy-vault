---
id: ADR-004
type: decision
role: packaging
tags: ["role/packaging"]
status: accepted
role_router: "[[roles/packaging]]"
related_tickets: ["[#10](http://127.0.0.1:3000/agy/nixos-config/issues/10)", "[#11](http://127.0.0.1:3000/agy/nixos-config/issues/11)"]
related_files: ["[[harvest-partial-declarative.sh]]", "[[splice-instrument.settings]]", "[[splice-user.reg]]"]
---
# ADR-004: Partial-Declarative Config Harvester for GUI & Wine State

**Role:** [[roles/packaging]]

## Context
GUI applications and Wine runtimes dynamically write state to home directory and registry hives, breaking pure declarative Nix reproducibility.

## Decision
1. Deploy `harvest-partial-declarative.sh` to periodically harvest critical mutable config files.
2. Filter ephemeral keys (timestamps, machine GUIDs, nonces) and store sanitized baselines under `/etc/nixos/config/partial-declarative/`.
3. Re-inject sanitized configurations during packaging derivation wrappers.
