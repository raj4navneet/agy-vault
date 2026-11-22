---
id: TB-001
type: traceback
role: orchestrator
tags: ["role/orchestrator"]
status: resolved
role_router: "[[roles/orchestrator]]"
related_ticket: "[#4](http://127.0.0.1:3000/agy/nixos-config/issues/4)"
affected_files: ["[[nix-rebuild.sh]]"]
error_signature: "PermissionDenied: cannot switch to system profile"
---
# TB-001: PermissionDenied Error Executing nix-rebuild

**Role:** [[roles/orchestrator]]

## Error Snippet
```text
building the system configuration...
updating GRUB 2 menu...
activating the configuration...
setting up /etc...
Permission denied: cannot switch profile /nix/var/nix/profiles/system to generation 142
```

## Root Cause
Rebuild invoked directly without appropriate sudo escalation or security wrapper permissions.

## Resolution
Configured passwordless sudo rules for `nixos-rebuild` and delegated rebuild requests through `agy-ask.sh`.
