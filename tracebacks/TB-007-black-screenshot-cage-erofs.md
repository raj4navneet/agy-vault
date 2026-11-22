---
id: TB-007
type: traceback
role: orchestrator
tags: ["role/orchestrator"]
status: resolved
role_router: "[[roles/orchestrator]]"
related_ticket: "[#34](http://127.0.0.1:3000/agy/nixos-config/issues/34)"
affected_files: ["[[proxies/agy-capture.sh.md]]", "[[proxies/agy-sandbox.sh.md]]", "[[proxies/agy-attach.sh.md]]"]
error_signature: "Error: EROFS: read-only file system, open '/home/navigator/.config/obsidian/obsidian.log'"
---
# TB-007: Black Screenshot in Headless Cage Due to EROFS & Missing Documents Symlink

**Role:** [[roles/orchestrator]]

## Error Snippet
```text
App threw an error during load
Error: EROFS: read-only file system, open '/home/navigator/.config/obsidian/obsidian.log'
    at Object.openSync (node:fs:622:18)
    at logger (/nix/store/...-obsidian-1.13.7/share/obsidian/app.asar/main.js:64:19)
Uncaught Exception:
Error: EROFS: read-only file system, open '/home/navigator/.config/obsidian/obsidian.log'
```

## Root Cause
When applications were captured inside `cage` within the Bubblewrap sandbox:
1. `agy-sandbox.sh` mounted the root filesystem as read-only (`--ro-bind / /`), leaving `~/.config` read-only. Applications attempting to create or open log files (such as `obsidian.log`) crashed on launch.
2. `agy-sandbox.sh` masked `~/Documents` with `--tmpfs ~/Documents`, preventing Obsidian from seeing the vault at `~/Documents/obsidian/agy_vault`.
3. When the child application crashed, `cage` remained running with an unmapped, solid black background. `grim` captured this black screen (producing identical 2,759-byte files), and `agy-capture.sh` had no health checks or black-screen validation.

## Resolution
1. Modified `scripts/agy-sandbox.sh` to remove blanket tmpfs masking of `~/Documents` and bind `~/.config/obsidian` read-write.
2. Updated `scripts/agy-capture.sh` to provide an ephemeral writable `XDG_CONFIG_HOME` shadow copy when `~/.config` is read-only, export `NIXOS_OZONE_WL=1` and `ELECTRON_OZONE_PLATFORM_HINT=wayland`, check child process liveness, and validate that the captured PNG contains non-zero pixel bytes.
3. Updated `scripts/agy-attach.sh` with a guard rejecting upload of solid black screenshots.
