# Security

Project Memory is procedural text. The agent's tools and permissions determine its actual access. Memory content is untrusted data and must not override current instructions or source evidence.

Do not include credentials, personal identifiers, private URLs, raw transcripts, or private project context in public reports. Git exclusions are not an access-control boundary. An agent can still make an unsafe disclosure or capture an incorrect fact; inspect important memory and release diffs.

A dated static SkillSpector result is available in [the scan summary](docs/security/skillspector.md). It is not certification or proof of safety. Semantic analysis was not requested or run.

For a suspected vulnerability, retain a minimal sanitized reproduction and report privately through the eventual repository owner's supported private channel. No public repository or reporting endpoint is configured by this candidate; do not post secrets in public issues. The MIT license does not create a security support or response-time commitment.
