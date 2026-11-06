# Focused testing policy

Owner direction: November 6, 2026. Apply to future work on this app to conserve coding credits while maintaining accuracy.

## Choose checks by risk

Before running checks, identify changed behavior, its callers/data flow, affected platforms, and the smallest meaningful verification set. State the selection and why it is sufficient. Inspect other platform consumers when behavior is shared; do not run unrelated platform suites merely because they exist.

- Documentation only: review the diff, instructions, links and formatting. No app build or regression suite unless the documentation changes an executable contract or build input.
- Copy, icons or local styling: check the affected screen and relevant accessibility/layout states; run existing focused checks where useful. Avoid a full native sweep.
- Feature or bug fix: reproduce the failure when practical, run affected unit/integration tests, and check the changed user journey plus likely adjacent regressions. Include loading, failure/retry, permissions and persistence where relevant.
- High risk: authentication, roles/privacy, money or clinical calculations, date/time rules, persistence/migrations, sync/conflicts/deletion, shared contracts, dependencies and build/signing configuration require broader affected-domain coverage and relevant integration/compatibility checks. Broaden across platforms that consume the change; use the full suite when impact cannot be bounded reliably.
- Release batch: run one broad regression pass for the affected application/platforms on the stable integrated candidate, with applicable release-build, signing/package and installation/launch checks. A web-only release does not require unchanged native suites. A documentation-only commit is not an app release. A small isolated hotfix may use a clearly justified focused release check with explicit residual risk; do not call an unrun full suite passed.

## Preserve evidence, avoid repeated work

Run focused checks during editing; reserve the broad pass for integration/release or material uncertainty. Reuse results only when the tested source and relevant dependencies, configuration, toolchain and fixtures remain equivalent. Record the tested SHA and explain any reuse after a later commit using the actual diff. Invalidate affected results and assess broader impact after code changes; never describe a stale run as testing the current source.

For a known bug, add a durable regression test when it guards meaningful behavior. Do not add tests that simply mirror an implementation, or create new tests for every reversible wording/documentation edit. Use the repository's actual commands and supported runtime; do not invent a passing test command when a suite does not exist.

## Diagnose failures before rerunning

Classify failures as product defect, test defect, environment/infrastructure issue, or unresolved. Retain the original failure and supporting evidence. Reproduce the failing case first; after an evidenced setup correction, rerun that case or stage. Do not repeatedly restart an entire suite, blindly retry until green, weaken assertions, or dismiss a genuine failure as flaky.

For simulator/UI work, check the intended device/runtime, awake and unlocked host when required, keyboard/size-class/window state, signing/automation permission, and exclusive simulator ownership. Reuse healthy build products when valid; clean/reinstall/rebuild only when needed. Optional whole-device diagnostics, screenshot tours, performance sweeps and live-service tests are opt-in unless necessary for the change.

If a run stalls or triage exceeds roughly ten minutes without useful new evidence, stop blind retries, report the blocker and next diagnostic step, and continue independent work. This is a troubleshooting checkpoint, not permission to bypass an unresolved release blocker.

## Keep costs and results visible

Prefer deterministic local fixtures and concise summaries. Do not use real notifications/messages, financial transactions, production writes or paid AI/API calls solely for routine tests without existing task authorization. Do not enable scheduled tests, change billing/CI gates, disable checks, or add agents merely to satisfy this policy.

In the PR or handoff, record: risk and affected surfaces; selected checks and tested SHA; pass/fail/skip/cancel results and elapsed time when available; unique product bugs versus test/environment fixes; reused evidence; and remaining gaps. Count distinct causes, not failed assertions or repeated runs, as bugs found. Report unavailable credit/token costs as unknown; elapsed test time is not a credit bill.

This owner-directed policy supersedes older blanket instructions to run every suite after every edit. Keep existing product invariants, task-specific safety checks, externally enforced CI requirements and release authorization rules. Do not ask the owner to re-approve routine test selection under this policy; explain the selection and proceed. Specific later owner instructions take precedence.
