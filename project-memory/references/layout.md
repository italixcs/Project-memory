# Compact layout

Start with one entry file. Omit empty sections; preserve existing conventions rather than rename them.

```markdown
# Project context
Project: safe label; scope: this checkout
Storage: local private / approved shared
Updated: date; observed revision/snapshot; relevant dirty state

## Goal and constraints
- Purpose and non-obvious approved constraints; link maintained requirements.

## Navigation
- [Design](../docs/design.md): canonical architecture and rationale.
- [Queue](queue.md): retry pitfall and an unresolved acceptance check.

## Decisions without another canonical home
- D-01 [active]: choice; why; source/date if known.
  Recheck when: concrete affected condition changes.

## Current handoff
- Goal / acceptance criteria:
- Observed completed work and relevant changed paths:
- Remaining / blockers:
- Verification: exact command, working directory, actual result and snapshot;
  or not run. Prefer links to maintained commands.
- Next executable step:
- Unverified or stale claims:
```

This is a shape, not a form to fill with guesses. Resolve paths relative to the memory file: root `docs/` is `../docs/` from `.project-memory/INDEX.md`, or `docs/` from a root context file.

Create focused topics only when needed:

```markdown
# Queue retry behavior
Scope: queue subsystem; verified at snapshot/date
Sources: relative source/config/test paths; stable doc section or issue

- [active] Retry only transport failures. Source: maintained queue design.
- [unverified] Previous session reported a duplicate-send race; reproduction
  unavailable. Do not present as confirmed behavior.
- Pitfall: success can be followed by an acknowledgement timeout.
  Reproduction/solution: link maintained test or fix.
- Recheck when: backend, acknowledgement policy, or retry rules change.
```

Keep entries independently understandable and link sources; avoid line-number-only pointers. Link ADRs rather than copy text. Use stable decision IDs where replacement/history needs them. Exclude large code excerpts, raw session logs, inventories, personal facts, and speculative roadmaps.

RAG or a personal knowledge tool could later index sanitized Markdown. That adds access, deletion, and freshness obligations. Do not integrate it or copy private project context into global personal memory by default.
