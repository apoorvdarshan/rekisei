# Security policy

## Supported versions
The current `main` branch is supported. Update to its latest tested commit.
Older snapshots do not receive separate security backports.

## Reporting a vulnerability
Report suspected vulnerabilities privately to **apoorv@fud-ai.app**, or use
GitHub's private vulnerability reporting option when available. Do not post
credentials, personal resume data or exploitable details in public issues.
Include the affected commit, impact, reproduction steps and a suggested fix.
Reports are triaged by Apoorv Darshan, the sole maintainer. The response target is
14 days; critical issues are prioritized immediately. Coordinate disclosure
until a fix is available. These are response targets, not a historical attestation.

## Trust boundaries
LaTeX input can read local files and may execute commands when shell escape is enabled. Compile only trusted sources; use `-no-shell-escape`, an isolated output directory, and a disposable environment for third-party templates. Never commit personal resume source or outreach logs to this public template. The skill is guidance, not a sandbox. The template implements no cryptography or password storage.

## Development and release checks
Use least privilege, validate external input, and review dependency advisories.
Every major change needs automated tests and static analysis before publishing.
Fix confirmed exploitable findings of medium or higher severity promptly; do not
leave known medium/high vulnerabilities unresolved for 60 days. Document security
fixes in CHANGELOG.md, including CVE identifiers when applicable. Dependencies
are monitored with Dependabot and CI audits where a package manifest exists.

Solo-maintainer policy: zero required approving reviews. Do not require code-owner
approval or last-push approval. Force pushes/deletions are blocked where the GitHub
plan supports protections. Automated profile commits must remain possible.

## Automated security analysis
CodeQL scans the Python template validator on pushes, pull requests and weekly.
CI separately validates the LaTeX source and compiles with shell escape disabled.
CodeQL does not analyze LaTeX. This template has no application input parser to
fuzz; no fuzzing integration is claimed. Required reviewer approvals remain zero
for the sole-maintainer workflow.
