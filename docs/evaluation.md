# Behavioral evaluation

Date: 2026-11-17. Target: initial candidate, identified by the [complete package manifest](package-manifest.json). This was a small Skill Bench diagnostic, not a maintained dataset or statistical benchmark. No target instructions changed after the version was frozen.

## Verdict

**Useful process consistency, with a narrow reconciliation advantage on these cases.** Both arms completed the requested software changes and recovered the prior decision. The independent anonymized reviewer tied capture/resume and the negative case, and narrowly preferred the skill arm for explicitly reconciling obsolete refresh and blanket-test-pass claims. This does not demonstrate universal quality gains or token savings.

## Method

Three paired scenarios used fresh independent worker histories, separate copies of identical synthetic projects and the same task prompts. The first scenario had two genuine stages: one pair prepared handoffs; a different fresh pair later resumed from only persisted project files and the second task. Session-1 completion notes and conversation histories were not supplied to session 2.

Eight worker jobs covered the paired scenarios (four for capture/resume, two conflict, two negative). A ninth fresh job performed the anonymized review. Additional targeted lifecycle checks are listed separately below. All workers inherited the same model/effort defaults; exact model settings were not exposed. No paid external inference was initiated.

Prompts, fixture-generation source, criteria, candidate hashes and run configuration were saved before worker execution. Identical independent output contracts were applied to both arms. A/B labels were randomly assigned separately for each case using the host's random source; the reviewer saved its verdict before the mapping was revealed. Case-local labels were decoded per case, not treated as one consistent overall A/B assignment.

**Isolation limitation:** fresh histories are real, but filesystem and host skill access are shared. Local catalog and workspace restrictions were instruction-only. Candidate workers received the package through an optional local catalog; baseline catalogs contained no added procedure. Host user skills were prohibited by the identical harness, but this was not an enforced access boundary. The reviewer was likewise restricted by instructions. Procedure/catalog packaging was omitted from its packet, but substantive output layouts and router text could allow inference. Call this a best-effort local-catalog routing comparison, not a clean isolated baseline or native automatic-discovery test.

## Cases and results

| Scenario | Baseline | Project Memory | Blind verdict |
| --- | --- | --- | --- |
| Two-session exporter handoff and requirement change | Preserved importer rationale in HANDOFF.md; fresh worker recovered it, added optional CSV and retained default JSON; independent contract passed | Preserved rationale in locally excluded index with a router; fresh worker recovered it, superseded the old restriction, added CSV and retained default JSON; same contract passed | Tie |
| Stale scheduler facts and contradictory notes | Corrected SQLite/configuration, applied 15 minutes, recovered UTC rationale; source checks passed; historical reconciliation less explicit | Same correct configuration and rationale; explicitly superseded five-minute claim and rejected unsupported blanket test-pass claim | Skill narrowly preferred |
| Nearby one-off code question | Correct `blue-desk` answer; source/context unchanged, no new project files | Same answer and unchanged files | Tie |

Exporter contracts checked byte-identical default/explicit JSON, header and row shape, commas/quotes/embedded newlines, empty CSV, negative quantities without new restrictions, and ValueError for unsupported formats. Final worker-created suites passed: skill 5 tests, baseline 8. Different test counts were not scored as a benefit. Both also passed the same independent contract. The actual audit-log importer was unavailable; no integration pass was claimed.

Scheduler contracts confirmed SQLite and 15 minutes; both final suites passed their one UTC test. Runtime storage and refresh-loop behavior were absent from the supplied project and remained unverified. The stale setup guide and alleged integration suite were unavailable/nonexistent. The unrelated branding topic and untrusted archived operator instruction were not copied into actionable handoffs.

The reviewer found no demonstrated critical failure. It correctly marked exact file-read selection, outside-workspace write absence, full execution/privacy compliance, and session-1 execution traces as insufficiently evidenced by the artifact packet. Absence of leaked content is not proof that it was never read. Selective retrieval cannot be called empirically verified without read traces.

## Representative prompts

The session-1 task said to prepare the exporter for another session, preserving the JSON-only audit-importer reason, offline/standard-library constraints, and negative-quantity rejection as an unapproved proposal, with no feature work.

The fresh session-2 task asked why JSON-only had been selected, approved optional CSV while preserving importer compatibility, specified exact API behavior, prohibited new quantity restrictions/dependencies, and requested verification plus refreshed context.

The conflict task asked to resume the scheduler, apply the newly approved 15-minute configuration, establish its backend from current sources, recover UTC rationale, and fix the existing context.

The negative task asked what `normalize_label("  Blue__Desk  ")` returns, briefly and without file changes. The function trims, lowercases, and replaces runs of spaces/underscores with a hyphen.

## Activation and efficiency

Local procedure availability was configured for the candidate, not proven through native host discovery. The produced private memory, updated reconciliation and handoff are application evidence. Complete tool-read traces were not available to the controller; exact invocation/read status and unwanted retrieval remain unknown. Neither negative worker created or edited project files.

Actual agent token consumption, execution time and cost telemetry were unavailable and remain **unknown**, not zero. No token estimate was derived from character counts. The entry-point bounds are design heuristics; no measured token-saving claim is supported. Installation/format checks do not establish lifecycle automation.

One run per arm per scenario was retained. Ties were accepted because objective completion was unambiguous; the small diagnostic was not expanded to seek a winner. No repeated attempt was discarded or selected as a best result. Comparative confidence is limited.

## Additional checks and limitations

- Complete six-file installation copy and no-overwrite guard: exercised in a disposable directory, preserving file bytes. This is packaging evidence, not a native host runtime test.
- Existing context reuse: both conflict outputs updated the established root file rather than create a competing bank.
- Private storage default: the candidate capture produced a locally ignored index, confirmed with Git. The baseline created ordinary documentation; the original synthetic task did not prohibit that layout.
- A targeted removal/derived-copy smoke check is reported in the [release verification record](verification.md). It is not part of the paired quality verdict.
- Concurrency races, tracked-memory guard behavior in an agent, worktree switching, real secrets, inaccessible persistent stores, and cross-device or cross-product continuation were not demonstrated by this diagnostic.

The observed results justify retaining the narrow lifecycle procedure. No behavioral change was justified merely to force a quality win. The next useful evidence would be a real project trial with host-supported read/token telemetry and enforced skill isolation, rather than more synthetic documentation cases.
