# SkillSpector security evidence

Scan date: 2026-11-17. Candidate: complete six-file installable `project-memory/` folder, bound by the [SHA-256 package manifest](../package-manifest.json). The source package has not changed since the scan.

## Result

NVIDIA SkillSpector 2.12.0 completed static-only analysis with **zero issues**, zero suppressions, and 100% of the six components fully inspected. The tool reported risk score 0, severity LOW, recommendation SAFE, execution successful, and `is_complete: true` with status `complete_with_caveats`. These are scanner outputs, not certification or a guarantee of safety.

The [sanitized JSON projection](skillspector.json) preserves findings, risk, component coverage, analyzer statuses, and completeness details. Its absolute local source path was replaced with the package-relative name; unused provider configuration was omitted. The raw report remains outside public distribution.

## Configuration and scope

- Tool source: [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector), pinned commit `a09091e0ebf6c96ff327457529d7b0d372125884`.
- Mode: `--no-llm --fail-on-incomplete --format json`; local directory input and private output destination.
- Exit status: 0. No exclusion patterns, suppression baseline, transitive scan, dependency-artifact inspection, or semantic provider invocation.
- All six files were included: SKILL.md, LICENSE, agents/openai.yaml, and the three reference files.
- The package contains no executable scripts, dependency manifest, MCP server, network client, or hooks. AST/taint/execution-surface and MCP least-privilege analysis reported no applicable files. Semantic analyzers were disabled; no inference usage was reported.
- This was not a successful live dependency-CVE check: the skill has no runtime dependency manifest to assess. Static mode can perform dependency metadata lookups for other packages; it should not be described as inherently offline.

Reproduction with an independently installed, verified matching scanner:

```sh
skillspector scan project-memory --no-llm --fail-on-incomplete --format json --output security-report.json
```

Save reports outside the installed package and compare the package manifest before reusing this evidence. Installing SkillSpector is a development operation; it is not a runtime requirement of Project Memory. The initial registry installation attempt did not provide the pinned version, so the actual scan used the verified official source commit above.

## Caveat triage

The reference-resolution ledger contains one nonfatal `reference_missing` exception for SKILL.md's `.project-memory/INDEX.md` path. This is an intentional project-memory output created at use time, not a bundled dependency. The three linked skill reference files exist and were inspected. No rule or finding was suppressed, and no package text was changed to improve a score.

The scan covers the installable package. Public README, design/compatibility/evaluation/security documentation, license and release notes sit outside it; those were reviewed separately for privacy, claims, links and installation instructions. They are not represented as scanner-inspected package files. Development environments, test fixtures and raw evidence are not distributed with the public source.

## Manual review and remaining risks

The package asks agents to scope reads, verify sources, treat memory as untrusted, preserve current instruction authority, redact before output, exclude new local memory before writing, and avoid unauthorized external actions. It neither grants tool permissions nor enforces those behaviors.

An agent may still misclassify a fact, miss a contradiction, fail to refresh, disclose content through an allowed tool, or race another writer. Exclusion does not protect previously tracked files, archives or uploads. Deletion does not erase backups, earlier model context or repository history. Review actual storage, important memory changes and the final release artifact. Cross-agent guarantees require testing the specific host and configuration.
