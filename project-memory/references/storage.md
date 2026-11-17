# Storage and privacy

Read before creating or changing a memory destination. Privacy depends on the storage and distribution route, not a Markdown label.

## Existing memory

Reuse the designated context file, memory bank, or tool index. Check its tracking and sharing mode first. Keep shared files limited to approved nonsensitive facts. For private handoff context, use a private sidecar with a distinct purpose; do not duplicate canonical decisions. Shared indexes must not expose private text, machine paths, or identifying pointers. Give the private location through the private session instead.

## New memory in a Git checkout

1. Resolve the checkout root. Inspect filenames, `git status --short`, and the destination. Check tracked memory with `git ls-files -- .project-memory`. If tracked, exclusion cannot protect it. Do not overwrite or untrack it automatically; use an approved private destination or resolve the sharing choice.
2. Default to `.project-memory/INDEX.md` in this checkout. Before writing content, resolve the local exclude file with `git rev-parse --git-path info/exclude`, inspect that destination, and append `/.project-memory/` only if absent. Preserve contents. Handle worktrees through Git's returned path, not an assumed `.git/` directory. Do not follow unexpected symlinks or write beyond authorized project/config scope.
3. Verify the intended file is ignored with `git check-ignore -- .project-memory/INDEX.md` and recheck that no memory files are tracked. If either protection fails, do not write private memory there. Use another verified private location or report the blocker. Exclusion reduces accidental staging; it is not encryption, access control, backup, or protection from force-adds and archive uploads.
4. Keep private memory out of releases, screenshots, scan uploads, attachments, and public docs. Review distribution separately: Git ignore/exclude rules do not constrain all packaging tools.

Do not add public ignore rules, change global Git settings, or install hooks just to initialize memory. An authorized short private host-context pointer can help discovery without becoming a second source of truth.

## Other environments

For non-Git projects, use a user-designated or host-provided private persistent folder scoped to that project. If no durable destination is known, ask before a dependent write; prepare a sanitized handoff meanwhile. Scratch storage may disappear. Without file tools an agent can produce text to save, but cannot demonstrate persistence.

Use a safe project label and relative source paths. Bind external private storage through the existing association mechanism; do not infer identity from a common folder name or mix clones/worktrees silently. Cross-device use needs an explicitly configured transfer mechanism. Do not invent a global registry.

## Sharing and removal

Use shared memory only through explicit user choice or an established approved convention. Review each entry for publication; never bulk-copy a private bank. Change storage through a reviewed move and update its private pointer, not two live copies.

Forgetting includes in-scope derivatives and incoming links; do not retain removed content in archives or reports. Local deletion cannot erase remote versions, backups, or previous model context. Disclose those limits. Handle credential exposure without repeating its value.
