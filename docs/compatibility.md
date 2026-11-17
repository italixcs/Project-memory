# Installation and compatibility

Checked against primary documentation on 2026-11-17. A matching directory layout is not evidence that every host will automatically select the skill.

## Install the complete folder

Copy `project-memory/` including all references and LICENSE. Do not install only SKILL.md, the whole source repository, or private project memories. Check for an existing skill with the same name before copying; do not overwrite it silently. Disable or remove duplicate versions deliberately.

From the extracted source root, on a POSIX shell, a project-local Codex copy can be prepared with:

```sh
mkdir -p .agents/skills
test ! -e .agents/skills/project-memory && cp -R project-memory .agents/skills/project-memory
```

Run this in the intended project, using the extracted `project-memory` source folder as the copy source (use its actual path if elsewhere). The no-overwrite guard intentionally fails when a version already exists. PowerShell users can copy the folder with their file manager; no shell script is required by the skill.

| Host/route | Destination or invocation | Evidence level |
| --- | --- | --- |
| Codex local project | `.agents/skills/project-memory/`; explicitly invoke `$project-memory` if discovery does not select it | Directory route documentation-checked; candidate behavior exercised through fresh Work-mode workers and a local catalog, not a native Codex CLI discovery test |
| Codex user-wide local | `~/.agents/skills/project-memory/` | Documentation-checked only |
| Claude Code local project | `.claude/skills/project-memory/`; `/project-memory` where native skills are enabled | Documentation-checked only; runtime not tested |
| Claude Code local personal | `~/.claude/skills/project-memory/` | Documentation-checked only; cloud/account skill synchronization is a separate route |
| ChatGPT Work Mode in this evaluation | Supplied local skill catalog plus file tools | Best-effort procedural diagnostic; automatic account installation/discovery not tested |
| Other ChatGPT environments | Use the available skill installation facility, or explicitly supply the complete instructions and relevant persisted files | Capability-dependent; no universal persistence, hooks or automatic selection claim |
| Other compatible agents | Load SKILL.md and its referenced files through the host's supported procedure mechanism | Manual-only until tested in that host |

Native display metadata in `agents/openai.yaml` is optional. Other hosts can ignore it. The common core uses only standard name/description frontmatter and relative resource links.

## First useful use

Ask: “Prepare this project for a fresh session. Preserve important decisions, unfinished work, and what still needs verification.” Explicitly select Project Memory if the host needs it.

Inspect the saved entry point and its privacy/storage mode. Start a genuinely fresh session with the same persisted checkout, then ask to resume a specific task. If the host does not discover local memory, provide its private entry point explicitly. A locally excluded file will not travel with a Git clone or push.

Use an existing short project-local router only within authorization. Do not paste private context into public AGENTS.md/CLAUDE.md or global agent instructions. The memory entry point remains a navigation aid; current instructions and source evidence retain their authority.

## Requirements and limitations

- File reading/writing is required for maintained memory; plain chat can only produce a handoff for someone else to save.
- Persistent storage and continuity of access belong to the host/user. This package cannot make scratch files durable.
- Git is optional overall, but the documented default local-exclusion workflow requires Git. Non-Git use needs a known private persistent project folder.
- No runtime interpreter, database, embeddings, server, network or account is required by the skill.
- Agents make semantic capture and reconciliation decisions. No deterministic guarantee of correct memory, complete forgetting, secrecy, or concurrent-write safety is offered.
- No native hooks, slash-command registration, startup injection, synchronization or RAG connector is installed by reading the instructions.

Primary documentation: [Agent Skills](https://agentskills.io/specification), [Codex skills](https://developers.openai.com/codex/skills/), [Codex project instructions](https://developers.openai.com/codex/guides/agents-md/), [Claude Code skills](https://code.claude.com/docs/en/skills), [Claude Code memory](https://code.claude.com/docs/en/memory).
