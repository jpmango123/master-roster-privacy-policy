# master-roster-privacy-policy coding instructions

## Focused testing — owner direction, November 6, 2026

Read [FOCUSED_TESTING.md](FOCUSED_TESTING.md) before choosing checks. Focused checks are the default; broaden for high-risk changes and once per affected release batch. This replaces older blanket run-everything requirements, while preserving product invariants and required CI checks.

For this static support/privacy site, check changed HTML, links, mobile readability and consistency with the app's published behavior. Native regression runs are unrelated to text-only site work.

## Codex investigation and completion handoff — owner direction, November 6, 2026

These rules supplement all existing AGENTS.md, nested instructions, CLAUDE.md, and FOCUSED_TESTING.md; preserve stricter project invariants and existing owner release authorizations.

- **Before edits:** identify the current branch/HEAD SHA, read applicable project instructions, inspect affected code/data flow, and preserve unrelated work. Scope parallel agents to non-overlapping files or worktrees; coordinate changes to shared contracts.
- **Root-cause discipline:** reproduce or substantiate a reported defect using source, logs, tests, or observations before claiming a cause. Clearly separate *verified cause*, *hypothesis*, and *unresolved*. Do not treat symptom-based guesses as facts or make speculative fixes.
- **Validation:** select focused checks according to FOCUSED_TESTING.md and risk. Record actual pass/fail/skip/unavailable results and the tested SHA. Never imply an unrun full suite passed; broaden checks for high-risk/shared-contract changes and stable release batches.
- **Completion handoff:** give a short report with (1) requested objective, (2) evidence/root cause or uncertainty, (3) files and user-visible behavior changed, (4) verification performed with SHA and gaps, (5) commit/branch/PR links and whether merged, deployed, TestFlight-available, and physical-device-verified **separately**, and (6) remaining risks and the single next action.
- **Keep context durable and lean:** update an existing README, progress note, issue, or handoff when appropriate instead of creating duplicate histories. Avoid secrets, personal data, unnecessary CI/paid service calls, unrequested production writes, and unrelated changes. Documentation-only edits require a documentation/diff review, not an app regression run.
