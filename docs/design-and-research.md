# Design and research

Research reviewed on 2026-11-17 through primary repository files, official documentation, GitHub MCP, and Context7. This is a design assessment, not a runtime comparison of the external products. Repository documentation can change after this review.

## Recommendation: build narrowly

Useful file-based memory already exists. Project Memory is justified as a small portable maintenance procedure for agents that have file access but no common memory lifecycle. Its contribution is explicit evidence, reconciliation, private defaults, and restrained retrieval. It does not introduce a new storage engine or claim a novel memory algorithm.

If a project already uses Serena or a working memory bank, keep its files and use this procedure only where it improves maintenance. Do not install a parallel bank. Native agent instructions remain useful routers; code, authoritative requirements, ADRs, and maintained docs remain their respective sources of truth.

## Existing approaches

| Approach | Capture, storage, retrieval | Updating, removal, contradictions | Assessment for this project |
| --- | --- | --- | --- |
| [Cline Memory Bank](https://github.com/cline/clinerules/blob/main/.clinerules/memory-bank.md) | Structured Markdown for brief, product, architecture, technology, active context, and progress; directs reading all core files. | Explicit documentation refresh; conflict and deletion policy largely depend on the agent. | Reuse explicit current-work handoffs. Avoid a mandatory six-file bank and full reads on every task. |
| [Serena memories](https://github.com/oraios/serena/blob/main/docs/02-usage/045_memories.md) | Named Markdown topics, project/global scopes, an index/reference model, deliberate reads, optional tool interface. | Edit/delete/rename tools and reference-integrity checks; configurable hidden/read-only topics. Semantic freshness still requires judgment. | Strongest conceptual match. Reuse human-readable topics and narrow references; require neither Serena nor its MCP runtime. |
| [Memory Bank Skill](https://github.com/fockus/skill-memory-bank/blob/main/SKILL.md) | Cross-agent bank, client adapters, lifecycle commands, optional capture and retrieval tools. | Drift, agreement/supersession and consolidation workflows; configurable hooks and coordination. | Broader engineering toolkit with more installation and maintenance surface. Do not reproduce its rules, graph tools, hooks, or command suite. |
| [Claude Code memory](https://code.claude.com/docs/en/memory) | User-authored CLAUDE.md instructions plus agent-written repository-scoped auto memory; compact index and topic files. | Agents edit memory; users can inspect it. Bounded startup loading encourages small indexes. | Reuse the existing destination when suitable. Native auto-loading is product-specific and is not provided by this skill. |
| [Codex instructions and skills](https://developers.openai.com/codex/guides/agents-md/) | Scoped AGENTS.md instruction discovery; skills supply procedures with progressive loading. | Ordinary file maintenance, not a universal cross-agent memory service. Instruction-size budgets apply. | Keep AGENTS.md short; do not turn remembered facts into higher-priority instructions or copy a whole bank into it. |
| [MCP reference memory server](https://github.com/modelcontextprotocol/servers/blob/main/src/memory/README.md) | Local JSONL knowledge graph with entities, observations, relations, search/read tools. | Explicit mutation/deletion tools, atomic writes and interprocess locking in the reviewed version. Meaning and contradiction resolution still need policy. | Appropriate when structured graph operations are needed. Server/process/protocol and identity scope add unnecessary dependencies here. |
| [Mem0](https://github.com/mem0ai/mem0/blob/main/README.md) | SDK/server/platform memory, extraction and retrieval, configurable models and storage. | Current documentation distinguishes open-source features from managed-platform algorithms and benchmark claims. | Better suited to applications implementing memory APIs. Models, embeddings and infrastructure exceed this skill's needs; no hosted signup or integration was performed. |
| [Claude-Mem](https://github.com/thedotmack/claude-mem/blob/main/README.md) | Automated observation, persisted sessions, compact retrieval indexes, and agent integrations. | Runtime settings, capture controls and optional shared/cloud features govern retention. | Automation can reduce forgotten handoffs, but adds runtime, provider, privacy and maintenance choices. Do not introduce automatic transcript capture for this scope. |
| Earlier Project Memory procedure, inspected locally | A compact checkout-verified context file, decisions, commands and current work. | Refresh rather than append; source checks and privacy reminders. | Retain those ideas. Extend explicit stale/conflict states, storage safeguards, selective topic loading and forget behavior. No private project material was imported. |

No external project code, prompts, templates, images, or runtime dependencies were vendored. The implementation is original procedural text informed by these design patterns and the user's earlier skill. External product claims above are documentation observations, not independent verification of their reliability or benchmark results.

## Architecture choices

| Option | Advantages | Costs and failure modes | Decision |
| --- | --- | --- | --- |
| One context file forever | Simple discovery and editing | Eventually crowds retrieval and mixes durable rationale with session status | Starting point only; split when evidence warrants |
| Compact entry plus optional Markdown topics | Inspectable, portable, selective reads, no runtime dependency | Agent must maintain links and freshness deliberately | Selected |
| SQLite/JSONL memory service | Structured queries and transactional machinery | Schema/tool dependency; still needs semantic reconciliation | No demonstrated need |
| Vector/graph/RAG service | Can search very large corpora | Index freshness, deletion propagation, access control, embedding/model/runtime costs | Deferred until measured retrieval failures justify it |
| Host lifecycle hooks and auto-capture | Can reduce omitted writes/reads | Host coupling, excess capture, failure handling and privacy exposure | Optional future host-owned integration, absent from this package |

## Minimal complete scope

The installable package contains SKILL.md, three conditional references, optional OpenAI display metadata, and MIT license text. It contains no scripts, hooks, APIs, database, model calls, networking, or automatic synchronization.

1. Resolve the existing entry point and storage boundary.
2. Read a compact index, then initially at most two relevant topics or sections.
3. Verify action-relevant memory against current source and requirements.
4. Capture only durable, non-obvious deltas with applicable provenance and invalidation conditions.
5. Reconcile affected claims and their dependents after change.
6. Replace the current handoff; compact or remove low-value material.
7. Remove requested information and in-scope derivatives rather than archive forgotten content.

The 80-line entry target and initial two-topic bound are heuristics, not context-window guarantees. Agents can expand when the task needs it. Not every bullet needs metadata: shared provenance can be grouped. Stable decisions do not expire automatically.

## Sources of truth and conflicting evidence

Memory is a derived navigation layer. Current user requirements describe intended behavior; source/config/tests establish observed implementation within their tested scope. A new requirement can supersede a remembered decision while the code still implements the old behavior. Preserve that gap rather than claiming completion or silently discarding the requirement.

Choose evidence applicable to the project and checkout, not the newest timestamp. Mark absent evidence unverified. Keep old test passes historical after relevant changes. Invalidate dependent security notes, compatibility assumptions, commands and next steps when their premise changes. Keep unrelated decisions intact.

## Storage and durability

For a new Git project, default to a per-checkout `.project-memory/INDEX.md` excluded locally before content is written. Check for tracked files first: exclusions do not untrack files. Reuse approved shared memory only with nonsensitive facts; private sidecars must have a distinct purpose. Existing systems do not need to migrate.

Files are editable and removable with ordinary tools. Git exclusion is an accident-prevention measure, not encryption or an access boundary. No skill can make ephemeral host files persistent. New sessions must have the persisted files and a discovery pointer or explicit upload. Concurrent edits require coordination; no lock or transaction guarantee is claimed.

## Automation boundary

| Behavior | Provided by the skill | Additional requirement |
| --- | --- | --- |
| Decide what to capture/reconcile | Agent procedure | Agent must apply it at meaningful changes/handoff |
| Write and retrieve memory | Agent using existing file tools | Authorized persistent storage and file access |
| Startup discovery | Instructions for a small router or explicit file supply | Host discovery or user invocation |
| Detect code/requirement changes | Evidence-directed rechecks | Agent must inspect relevant current sources |
| Automatic pre-compaction backup, lifecycle hooks | No | Separately configured, tested host integration |
| Cross-device sync, RAG, personal second brain | No | Explicit external system with its own access/deletion rules |

## Maintenance

Treat instruction changes as behavioral changes. Keep a frozen package identity for evidence, run the native validator and affected checks, then a proportional behavioral diagnostic. Re-scan changed distribution content. Retain failures and uncertainty. Remove ineffective instructions instead of growing a framework of exceptions. Prefer existing tools for scanning, evaluation and skill authoring.
