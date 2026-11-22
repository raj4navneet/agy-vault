---
id: TB-006
type: traceback
role: packaging
tags: ["role/packaging"]
status: resolved
role_router: "[[roles/packaging]]"
related_ticket: "[#31](http://127.0.0.1:3000/agy/nixos-config/issues/31)"
affected_files: ["[[splice-instrument.settings]]", "[[registry-patches.reg]]"]
error_signature: "ALSA/PipeWire: pcm underrun; buffer size mismatch"
---
# TB-006: Wine WASAPI Audio Buffer Underrun and Latency Lag

**Role:** [[roles/packaging]]

## Error Snippet
```text
pw.audio: underrun in stream 'Splice INSTRUMENT': requested 4096 frames, got 1024
winealsa: audio thread buffer underrun detected, latency spike > 1200ms
```

## Root Cause
Wine WASAPI default buffer size mismatched PipeWire quantum, causing continuous underruns and perceived UI/playback lag.

## Resolution
Configured DirectSound 48kHz audioSetup block in `INSTRUMENT.settings` and tuned registry settings for persistent low-latency WASAPI buffer.
