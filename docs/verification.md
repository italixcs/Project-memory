# Release verification

Candidate 0.1.0, checked 2026-11-17. Evidence identifies the complete installable package through [SHA-256 hashes](package-manifest.json).

| Check | Status | Scope and limit |
| --- | --- | --- |
| Native skill initializer and validator | Passed | Initialized and validated the authoring directory; required metadata and naming accepted. Final source copy matches it byte-for-byte. |
| Relative package and documentation links | Passed | Local links outside code examples resolve; conceptual/runtime paths in template examples are intentionally not bundled. |
| Complete installation copy | Passed | Six files copied to a disposable `.agents/skills/project-memory/` destination and matched source bytes; repeat no-overwrite guard returned its expected nonzero status. No native agent startup was tested. |
| Behavioral comparison and independent reviewer | Completed, best effort | Three paired scenarios including a two-stage fresh-session continuation. See [evaluation](evaluation.md); shared access prevents clean isolation claims. |
| Additional removal lifecycle | Passed | One fresh independent worker removed a synthetic personal aside and its duplicate older note, repaired links, and preserved offline architecture/rationale. Controller confirmed the marker absent from all in-scope project text and source bytes unchanged. No assertion about history, external stores, or real secrets. |
| SkillSpector | Passed with documented caveat | Static scan of all six package files; zero issues/suppressions; one expected runtime-output reference-resolution caveat. See [security](security/skillspector.md). |
| Privacy and release contents | Passed within inspected scope | Public files checked for credentials/private context, signed URLs, environment-specific paths, test markers, private identifiers and raw worker/controller evidence. No private project source imported. Pattern checks supplement manual review, not proof of absence. |
| Licensing and dependencies | Prepared | MIT license included in source root and standalone package. No third-party implementation or template redistribution and no runtime dependencies. |
| Host installation routes | Documentation-checked | Codex and local Claude Code destinations checked against primary docs. Other hosts manual/capability-dependent; native host discovery unverified. |
| README presentation | Text/link reviewed | Restrained native Markdown. No live GitHub, mobile/light/dark screenshot or visual-render verification is claimed. No decorative banner was needed. |
| Remote actions and account installation | Separate authorization | The repository owner subsequently authorized committing and pushing this candidate to main. Tagged releases, visibility changes, and permanent skill installation remain separate actions. |

The candidate is usable within the documented file-access procedure. It is prepared for a scoped public release review, not certified for every host. Enforced isolation, exact token/read traces, native discovery, automatic refresh, concurrent writers and cross-device persistence remain unverified or outside scope.

## Prepared publication metadata

Suggested repository description: “Portable project-memory lifecycle for AI agents: verified context, selective retrieval, reconciliation, and session handoffs.”

Suggested topics: `agent-skills`, `project-memory`, `context-engineering`, `ai-agents`, `markdown`.

These are proposed values only; no GitHub settings or destination have been created. Before authorized publication, confirm the destination, compare package hashes, review final distribution, and keep private evidence out of the release. Do not label a future changed package as covered by these results without checking the affected evidence.
