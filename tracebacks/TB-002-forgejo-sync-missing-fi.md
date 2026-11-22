---
id: TB-002
type: traceback
role: orchestrator
tags: ["role/orchestrator"]
status: resolved
role_router: "[[roles/orchestrator]]"
related_ticket: "[#5](http://127.0.0.1:3000/agy/nixos-config/issues/5)"
affected_files: ["[[forgejo-sync.sh]]"]
error_signature: "syntax error: unexpected end of file (expecting 'fi')"
---
# TB-002: Bash Syntax Error: Missing fi in forgejo-sync.sh

**Role:** [[roles/orchestrator]]

## Error Snippet
```text
/etc/nixos/scripts/forgejo-sync.sh: line 79: syntax error: unexpected end of file
fatal: script execution aborted before push
```

## Root Cause
An unclosed if-block in credential validation caused bash parser failure.

## Resolution
Inserted closing `fi` and added mandatory `bash -n` static analysis in all sync and automation scripts.
