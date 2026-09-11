# Evidence Loop: staged validation design

## Status

Proposed scaffold; no product implementation authorized. The outcome may be onboarding fixes, a bounded Evidence Loop release, further discovery, or no new feature.

## Product hypothesis

Technical teams will repeatedly use E-GEO to preserve AI-answer evidence, choose reviewable interventions and compare later observations. A better content score is not evidence of better real-world visibility.

## Phase 1 — Reliable baseline

Audit `pyproject.toml`, the PyPI wheel, current source, `README.md`, `docs/` and `site/`. In a temporary virtual environment outside the repository, install the published package and exercise the documented CLI, runtime discovery and loop workflow with an isolated EGEO_HOME. Test availability of packaged collectors, templates, prompts and ledger support, not just module names. Compare with a source installation in a separate environment.

Produce a command/exit-code/result matrix with artifact version and digest, source SHA, missing resources, documentation differences and limits. Run existing tests; distinguish offline fixtures from live checks. Record actual cost/latency when available; unknown is not zero. Never infer a required version bump from release dates alone.

Gate B: baseline evidence reviewed; critical first-use failures have a prioritized fix plan. No feature-scope approval implied.

## Phase 2 — External validation and distribution

Proposed pilot: three consenting external users on distinct projects, with a second observation session after an agreed interval. This is a discovery cohort, not statistical validation. Owner approves recruitment and any API budget first. Record time to first useful result, assistance required, failure points, an example decision influenced by evidence and whether a second session occurred. Non-return and negative feedback remain in the record. Do not collect private content or identifying data in the public repo.

Complete a literal case-study article for approval; preserve its dated observation window and caveats. Submit/publish only with approval of that exact artifact. No automatic own-awesome-list, Product Hunt or additional comparison-page campaign.

Gate V: owner reviews anonymized pilot findings and chooses onboarding-only fixes, a bounded release, further discovery or stop. Repeat use and decisions matter; stars do not unlock this gate. A release recommendation should include at least two independently observed useful workflows and a recurring unmet need; this is a proposed decision aid, not proof of market fit.

## Phase 3 — Conditional release

Reuse project.yaml, EGEO_HOME, collectors and the outcome ledger. Exact CLI syntax and module changes follow the baseline audit, not this scaffold. Candidate scope:

1. Versioned query configuration with stable query IDs and branded/generic/technical segments.
2. Measurements classified as error, empty, valid_absent or valid_present; preserve timestamp, provider/model, query-set version, answer evidence, source URLs and run identity. Distinguish API products from consumer search interfaces.
3. Reproducible comparisons using compatible query IDs/configuration. Report valid and expected denominators plus missing coverage. Invalid samples cannot become zero visibility; configuration changes break direct trend comparability unless explicitly bridged.
4. Reviewable interventions linked to the existing ledger; distinguish proposed, approved, actually applied and observed. No publisher or automatic mutation.
5. Local JSON and Markdown evidence exports; no dashboard. Secrets and private inputs remain local, and public exports require explicit redaction/approval.

Gate R: approve a follow-up implementation delta with exact files, TDD tests, compatibility/migration plan and release acceptance criteria. Do not implement Phase 3 merely because this planning PR merges.

## Phase 4 — Expansion decision

Review repeat use and concrete requests. Prioritize onboarding, measurement depth or hosted-operation discovery accordingly. No SaaS or open-core work without a separately approved demand-based proposal.

## Risks and constraints

- External citation changes may reflect model, retrieval, competitors or crawl changes; before/after comparison is observational, not causal attribution.
- Keep historical invalid snapshots intact, with an append-only invalidation record; reruns use unique IDs and cannot overwrite history.
- Keep the personal visibility script outside the OSS repo until its reusable logic and dependencies are audited. Do not copy credentials or user-specific paths into the package.
- No new MCP server, dashboard, scheduler, automatic posting or fabricated outcome data.
- Documentation may drift independently of source; archive old OpenSpec changes only after auditing their actual completion in a separate cleanup.
