---
id: PROJECT-DOC-GUIDE
type: knowledge
role: orchestrator
updated: 2026-10-27
tags: ["dmb/knowledge", "project/doc-guide", "role/orchestrator"]
description: "Style, length budgets, Obsidian backlink conventions, and hygiene rules for .vault/."
---
# Doc Guide — Vault & Memory Bank Hygiene

> **Purpose**: Style, length budgets, Obsidian backlink conventions, and hygiene rules for `.vault/`.
> **When to use**: Consult whenever authoring, updating, or reviewing notes in `.vault/`.

---

## 1. Core Principles

DMB notes are loaded into agent context windows and rendered into Obsidian knowledge graphs. Concise, dense, well-structured notes maximize LLM reasoning bandwidth and keep graph visualizations navigable.

1. **One Purpose Per Note**: Every file must address a single conceptual scope (one ADR, one traceback, one core domain, or one proxy).
2. **Sub-10ms Wikilink Graph & Role Segregation**: Use Obsidian wikilink syntax (`[[TargetNote]]` or `[[folder/TargetNote]]`) to connect interrelated files. Keep domain-specific ADR, proxy, and traceback links routed through their respective **Role Router** (`roles/<role>.md`) so `INDEX.md` and `project/*` do not create cross-domain star-hub entanglement.
3. **Budget Discipline**: Target length budgets prevent notes from degrading into unreadable essays. When a note approaches its limit, split by sub-topic.

---

## 2. File Length Budgets

| Note Type | Target Lines | Purpose |
| :--- | :--- | :--- |
| `INDEX.md` | 60–150 lines | Central directory and operation-scoped discovery matrix. |
| `project/brief.md` | 60–120 lines | 30-second system understanding. |
| `project/domain.md` | 80–160 lines | Domain entities, business rules, and lifecycles. |
| `project/doc-guide.md` | 70–150 lines | This hygiene and style manual. |
| `technical/stack.md` | 70–160 lines | Comprehensive technology and dependency inventory. |
| `technical/architecture.md` | 100–200 lines | System design layers, data flows, and IssueOps pipeline. |
| `tasks/process.md` | 70–150 lines | Operational procedures for the RAM layer. |
| `roles/<role>.md` | 40–120 lines | Domain-specific role router and backlink index. |
| `decisions/ADR-*.md` | 40–120 lines | Architectural decision records (context, decision, consequences). |
| `tracebacks/TB-*.md` | 40–100 lines | Incident post-mortems with stack traces and root-cause fixes. |
| `proxies/<file>.md` | 20–50 lines | 1-hop proxy note for backlinked system files. |
| `tasks/work/<slug>.md` | 30–150 lines | In-flight working scratchpad (RAM layer). |
| `tasks/log/<slug>.md` | 15–50 lines | Permanent chronicle of completed ticket or feature. |

---

## 3. Note Structure & Frontmatter Standards

Every note in `.vault/` must open with a standard YAML metadata header:

```yaml
---
id: <UNIQUE_ID>
type: <index | role_router | adr | traceback | file_proxy | knowledge | state | work | log>
role: <nix-config | orchestrator | packaging | dev>
updated: YYYY-MM-DD
tags: ["role/<role>", "dmb/<layer>"]
description: "<Concise summary of file contents and operational scope>"
---
```

---

## 4. Obsidian Backlinking Protocol

- **Relative Wikilinks**: Prefer standard wikilinks without absolute disk paths:
  - Correct: `[[technical/stack]]`, `[[ADR-001-hybrid-memory]]`, `[[agy-sandbox.sh]]`
  - Incorrect: `file:///etc/nixos/.vault/...` or `@technical/stack.md`
- **1-Hop Backlink Querying**:
  Before refactoring an existing script or module `foo.ext`, agents query:
  ```bash
  rg "\[\[foo\.ext\]\]" .vault/
  ```
  This immediately surfaces all ADRs, past bugs, and role routers linked to that file in <10ms.

---

## 5. Content Discipline

- **Bullets Over Long Paragraphs**: Keep points short and structured.
- **Explain "Why", Not "What"**: Code shows *what* happens; memory notes record *why* design decisions were made.
- **Zero Redundant Duplication**: Link to existing Role Routers, ADRs, or proxies rather than repeating architectural decisions.
- **Tickets Hold the Essay**: Comprehensive debugging output and terminal conversations belong in Forgejo issue comments, not bloated into permanent `.vault/` notes.

---

## Cross-References
- Root Manifest: [[INDEX]]
- System Brief: [[project/brief]]
- System Domain: [[project/domain]]
- Technology Stack: [[technical/stack]]
- RAM Process: [[tasks/process]]
