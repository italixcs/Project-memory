# Project Memory

A portable AI agent skill for recovering verified project context across sessions.

Preserve decisions and their reasons, unfinished work, non-obvious solutions, and the changes that make old information stale. Keep source files and maintained documentation authoritative. Start with a compact Markdown entry point and add focused topics only when needed.

[Installation](docs/compatibility.md) · [Design and research](docs/design-and-research.md) · [Evaluation](docs/evaluation.md) · [Security](docs/security/skillspector.md) · [Verification](docs/verification.md)

## What it changes

A previous session records why an exporter uses JSON. A later session approves optional CSV. Project Memory guides the agent to recover the original importer-compatibility reason, preserve JSON as the default, mark the old CSV prohibition superseded, implement the new requirement, and leave a handoff tied to checks actually run.

That sequence was exercised with fresh worker histories and persisted files in the [evaluation](docs/evaluation.md). The baseline also completed it; no superiority or token-saving claim is made.

## Try it

Copy the complete `project-memory/` folder to the skill location supported by your agent. For a local Codex project, the documented destination is `.agents/skills/project-memory/`; for local Claude Code, `.claude/skills/project-memory/`. Check for duplicates first. See [platform routes and their evidence levels](docs/compatibility.md).

Then ask:

> Prepare this project for a fresh session. Preserve the important decisions, unfinished work, and what still needs verification.

To resume:

> Pick up the export feature. Recover the earlier decision, verify the current source, and continue the remaining work.

Explicitly select the skill if your host does not choose it. The next session needs the same saved files, or an explicit copy of the relevant context. Installation is not automatic persistence.

## Memory that can be maintained

- Reuse an existing context file or memory system instead of creating a duplicate.
- Read a small entry point and relevant topics, then verify action-relevant facts against current sources.
- Separate desired behavior, actual implementation, proposals, and verified results.
- Refresh affected entries and dependent assumptions; remove completed work and low-value history.
- Keep new memory local and excluded from Git by default; inspect sharing before writing.
- Forget requested entries and in-scope derivatives without hiding them in an archive.

> [!NOTE]
> Local exclusion reduces accidental staging. It does not encrypt files, protect uploads, or transfer memory to another device. See [storage safeguards](project-memory/references/storage.md).

## Scope and evidence

No server, database, vector store, external API, transcript recorder, hooks, or runtime scripts. Git is optional except for the documented local-exclusion route. The agent must deliberately apply the procedure; host automation is separate.

The package passed structural validation and a static SkillSpector scan. [Security evidence](docs/security/skillspector.md) records the exact scope and caveats. Behavioral evidence comes from a small best-effort comparison with fresh workers and an independent anonymized reviewer. Native discovery, other host runtimes, concurrent writes, and cross-device continuity remain unverified.

## Develop or adapt

Keep agent instructions in `project-memory/`; public documentation stays outside it. Do not add generated project memories or raw evaluation traces to this repository. For changes to the procedure, validate the complete package, test the affected behavior with realistic tasks, and rescan the final distribution. Use existing validators and scanners rather than adding another framework.

[MIT license](LICENSE). No external implementation code or templates are bundled. Reviewed approaches and source links are in the [research notes](docs/design-and-research.md).
