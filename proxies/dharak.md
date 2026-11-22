---
id: PROXY-dharak
type: file_proxy
file_path: "/home/navigator/agy-workspaces/dharak"
role: dev
tags: ["file_proxy", "role/dev"]
role_router: "[[roles/dev]]"
last_updated: "2026-11-10"
---
# File Proxy: `dharak`

## Metadata
- **Path on Disk:** `/home/navigator/agy-workspaces/dharak`
- **Domain Role:** [[roles/dev]]
- **Category:** Independent Dev Project / Asset Librarian

## Overview & Purpose
Universal Git-backed asset librarian, 2012 iTunes 11 chameleon expanded album grid, and Pixar Tractor boolean query engine (DQL) written in Rust (`axum`, `notify`, `image`, `tokio`) and Svelte 5.

## Key Interfaces & Exports
- `Daemon Port:` `http://127.0.0.1:7700` (`ws://127.0.0.1:7700/ws`)
- `CLI binary:` `dharak --register-asset <filepath>`
- `REST endpoints:` `GET /api/query?dql=...`, `POST /api/albums`, `POST /api/assets/checkout`

## Architectural References & Decisions
- [[technical/rachna-codex]]
- [[tickets/ISSUE-50]]
