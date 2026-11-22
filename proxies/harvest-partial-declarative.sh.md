---
id: PROXY-harvest-partial-declarative.sh
type: file_proxy
file_path: "/etc/nixos/scripts/harvest-partial-declarative.sh"
role: packaging
tags: ["file_proxy", "role/packaging"]
role_router: "[[roles/packaging]]"
last_updated: "2026-10-27"
---
# File Proxy: `harvest-partial-declarative.sh`

## Metadata
- **Path on Disk:** `/etc/nixos/scripts/harvest-partial-declarative.sh`
- **Domain Role:** [[roles/packaging]]
- **Category:** State Harvester Utility

## Overview & Purpose
Inspects mutable user configurations (Wine registry, audio preferences), sanitizes machine-specific keys, and copies baselines into /etc/nixos/config/partial-declarative/.

## Key Interfaces & Exports
- `harvest-partial-declarative.sh: Run harvester across targeted apps`

## Architectural References & Decisions
- [[ADR-004-partial-declarative-harvesting]]
