---
id: TB-004
type: traceback
role: packaging
tags: ["role/packaging"]
status: resolved
role_router: "[[roles/packaging]]"
related_ticket: "[#24](http://127.0.0.1:3000/agy/nixos-config/issues/24)"
affected_files: ["[[splice-instrument.sh]]", "[[splice-instrument.settings]]"]
error_signature: "Spitfire ERROR #4: Query failed for IR ID 1608633 against INSTRUMENT_Common_IR.db"
---
# TB-004: Spitfire Audio Engine Error #4 Missing Impulse Response DB

**Role:** [[roles/packaging]]

## Error Snippet
```text
[12:34:56] [Spitfire] ERROR #4: Query failed for IR ID 1608633
[12:34:56] [AudioEngine] Failed to initialize convolution reverb. Halting audio thread.
[12:34:57] [UI] Blank white window rendered; engine frozen.
```

## Root Cause
Splice INSTRUMENT required sample Impulse Response ID 1608633 which was absent from default user SQLite database.

## Resolution
Automated SQLite query patch in `splice-instrument.sh` inserting ID 1608633 pointing to container 1, and set `defaultIgnoreMissingSamples=1` in `INSTRUMENT.settings`.
