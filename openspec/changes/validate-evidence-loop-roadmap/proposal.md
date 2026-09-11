# Change: Validate the Evidence Loop roadmap before expanding the product

## Why

E-GEO needs a verified installation baseline and evidence of repeat external use before selecting its next release. Repository traffic and AI mentions do not demonstrate adoption or causal improvements. This proposal defines a staged decision process, not permission to build a new platform.

## What Changes

- Establish a reproducible baseline across the published wheel, source, documentation and first-use workflow.
- Validate usefulness with external projects and distribute the existing case study only after explicit owner approval.
- Define a conditional Evidence Loop release: configure queries, measure, propose an intervention, approve, remeasure and compare evidence.
- Separate missing observations from valid absence and branded discovery from generic discovery.
- Require a written owner decision before implementation scope, release version or hosted expansion is selected.

## Impact

- New planning capability: `evidence-loop-validation`.
- Reuse `egeo/workspace.py`, `egeo/loop.py`, `egeo/decide.py`, collectors and existing project configuration. No competing workspace, ledger or scheduler.
- Related proposals: `add-geo-loop`, `add-portable-project-config`, `add-loop-decision-layer`. Their implementation must be audited before adding duplicate functionality.
- This change contains documentation only. No runtime code, dependencies, cron changes, telemetry, publishing or deployment.

## Approval boundaries

Approval of this scaffold does not approve a feature implementation, public case-study distribution, recruitment messages, merges, package release or paid services. Owner approval must reference the concrete scope or artifact; silence is never approval.

## Evidence corrections

- Inspection of the published egeo 2.0.0 wheel found loop/workspace code and decide references. Do not claim those capabilities are absent from PyPI; verify functional completeness in isolation.
- Empty responses in the September 7 snapshot make that run invalid for visibility conclusions. Root cause remains unverified.
- Stars, clones and ChatGPT referrals are interest signals, not active users or proof of organic citations.
- No release number or launch date is committed by this proposal.
