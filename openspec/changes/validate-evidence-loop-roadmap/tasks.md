# Tasks and evidence gates

All boxes below describe future execution. Creating this scaffold does not complete them.

## 1. Baseline (before feature selection)
- [ ] 1.1 Record source SHA, wheel version/digest and documentation surfaces.
- [ ] 1.2 Install the published wheel in an isolated environment outside the source tree; record CLI help, runtime and documented loop command results.
- [ ] 1.3 Exercise fixture workflows in a temporary EGEO_HOME; verify packaged collectors/prompts/resources and inspect produced evidence.
- [ ] 1.4 Repeat against source in a separate environment and compare behavior.
- [ ] 1.5 Run `python -m unittest discover -s tests -v` after confirming repository test conventions; run the documented additional validation scripts as applicable. Save results without claiming a count in advance.
- [ ] 1.6 Audit `tests/test_cli.py`, `tests/test_project_config.py`, `tests/test_decide.py`, `egeo/loop.py`, `egeo/decide.py`, `egeo/workspace.py` and `collectors/` for reusable behavior and gaps.
- [ ] 1.7 Diagnose the external measurement runner using sanitized responses; propose an append-only invalidation for the empty snapshot, without overwriting it or altering crons.
- [ ] 1.8 Produce `baseline.md` with evidence, first-use friction and prioritized fixes; obtain Gate B review.

## 2. User validation and approved distribution
- [ ] 2.1 Prepare a consent/recruitment packet, observation worksheet and bounded API budget for owner approval.
- [ ] 2.2 Observe first use on three external projects; record assistance, time, errors and useful outputs without public PII.
- [ ] 2.3 Observe a second session and decision use; record non-return honestly.
- [ ] 2.4 Prepare the complete case-study article and canonical URL for explicit publication approval; do not treat a reuse note as a finished draft.
- [ ] 2.5 Produce anonymized `validation-findings.md`; owner chooses proceed, onboarding-only, further discovery or stop (Gate V).

## 3. Conditional implementation planning (not yet authorized)
- [ ] 3.1 Inventory existing commands/ledger schemas before choosing CLI syntax or new files.
- [ ] 3.2 Write a follow-up implementation delta and migration plan after Gate V; choose version only after compatibility review.
- [ ] 3.3 Specify RED-GREEN-REFACTOR tests for malformed responses, HTTP errors, empty answers, valid absence/presence and partial coverage.
- [ ] 3.4 Specify tests for query-set changes, segments, source provenance, distinct rerun IDs and immutable historical evidence.
- [ ] 3.5 Specify tests linking proposed/approved/applied interventions to observations without automatic application or causal claims.
- [ ] 3.6 Specify JSON/Markdown export, secret-redaction and old-workspace compatibility tests, plus wheel-installed end-to-end acceptance.
- [ ] 3.7 Obtain Gate R scope approval before any feature implementation.

## 4. Post-release decision (conditional)
- [ ] 4.1 Verify actual shipped installation and repeat-user outcomes; distinguish release availability from adoption.
- [ ] 4.2 Decide onboarding, depth, hosted discovery or stop from real usage; keep merge, release and publication separately owner-gated.

## Scaffold validation

Run `openspec validate validate-evidence-loop-roadmap --strict --no-interactive` and `git diff --check`. These validate the proposal, not the product or the future tasks above.
