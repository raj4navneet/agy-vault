---
id: TB-005
type: traceback
role: orchestrator
tags: ["role/orchestrator"]
status: resolved
role_router: "[[roles/orchestrator]]"
related_ticket: "[#23](http://127.0.0.1:3000/agy/nixos-config/issues/23)"
affected_files: ["[[configuration.nix]]", "[[default.nix]]"]
error_signature: "systemd-sleep: System entered sleep.target; session killed"
---
# TB-005: Catastrophic System Sleep Dropping Headless Daemon Sessions

**Role:** [[roles/orchestrator]]

## Error Snippet
```text
Oct 24 19:12:01 nixy systemd[1]: Reached target Sleep.
Oct 24 19:12:01 nixy systemd[1]: Starting System Suspend...
Oct 24 19:12:05 nixy kernel: PM: suspend entry (deep)
Oct 24 19:12:06 nixy tailscaled[1422]: connection dropped, reconnecting...
Oct 24 19:12:07 nixy agy-orchestrator[1646]: socket broken
```

## Root Cause
GNOME power daemon / laptop lid events invoked systemd sleep target, aborting running builds and socket listeners.

## Resolution
Masked `sleep.target`, `suspend.target`, `hibernate.target`, and `hybrid-sleep.target` via declarative NixOS systemd options.
