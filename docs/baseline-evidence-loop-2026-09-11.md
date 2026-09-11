# Evidence Loop baseline — published package vs source

**Date:** 2026-09-11 · **Phase:** 1 of `validate-evidence-loop-roadmap` (merged in #34) · **Author:** Hermes (automated baseline, human review pending)

**References:**

- Source: `origin/main` @ `a5af9daa06f4487f6b59b5ac4476391b0721713d`
- Published artifact: PyPI `egeo` 2.0.0, wheel `egeo-2.0.0-py3-none-any.whl`, SHA-256 `157312df481ce69852e6db06c18f4df310c9aa52b581b58e5ea18419ee0e2613`
- Environments: two isolated venvs under `/tmp`, outside the source tree; `EGEO_HOME` pointed at disposable directories

## 1. Command matrix

| Command | Wheel (PyPI 2.0.0) | Source (`origin/main`) |
|---|---|---|
| `egeo --help` / `--version` | ✅ `egeo 2.0.0` | ✅ |
| `egeo runtimes` | ⚠️ `python` runtime reports **unavailable** | ✅ `python` runtime **available** |
| `egeo optimize sample.md` (mock) | ❌ **exit 1** — `FileNotFoundError: site-packages/prompts/ranker_system.txt` | ✅ score 7/100, rank #4 → #1, all outputs written |
| `egeo evaluate --dataset …` (mock) | ❌ **exit 1** — same missing `prompts/` | ✅ `avg_rank_improvement 2.0, n=7, win_rate 1.0` (mock, positive by construction) |
| `egeo loop doctor` (fresh `$EGEO_HOME`) | ❌ **FAIL: missing file: SUBSTRATE.md** | ✅ bootstraps workspace incl. `SUBSTRATE.md` |
| `egeo loop collect serp --fixture …` | ❌ **exit 1** — `FileNotFoundError: collectors/serp.py` | ✅ writes JSONL observation + LOG.md line (fixture mode) |
| `egeo loop decide --dry-run` | ❌ blocked — requires `project.yaml`, but `examples/project.yaml` is not in the wheel | ✅ (with `project.yaml` present) |
| `egeo loop run egeo-core --dry-run` | ✅ prints run plan | ✅ |

**Verdict:** the published PyPI package is broken for every core workflow (`optimize`, `evaluate`, `loop collect`, `loop decide`, clean `loop doctor`). Only `--help`, `--version`, `runtimes` and `loop run --dry-run` work. Root cause: `pyproject.toml` ships `packages = ["egeo"]` + `py-modules = ["geo_eval", "llm_client"]`, but the runtime reads `prompts/`, `collectors/`, `SUBSTRATE.md` and `examples/` as loose repo-root files, and none are packaged.

## 2. Test suite and validators (source env)

- `python -m unittest discover -s tests -v` → **12 tests, OK** (`test_cli.py`, `test_decide.py`, `test_project_config.py`).
- `scripts/validate_skills.py` → 5 skill files, 0 errors.
- `scripts/validate_jsonld.py` → requires explicit files/`--dir` (no default run; usage printed).

## 3. External visibility measurement loop (task 1.7)

- **Diagnosis of the 2026-09-07 snapshot:** the runner treated an empty answer as a valid negative. Whatever AIsa/Sonar returned that day did not match the script's `success is False` check, so all 10 queries were recorded as `answer_chars: 0` and the cron reported "ok". Verified today that the client is healthy (returns `choices`/`search_results` normally).
- **Fix applied** (`~/.hermes/scripts/egeo_visibility_measure.py`, outside this repo): empty answers are now `error: empty_answer`; if fewer than half the queries return usable answers, the snapshot is written as `*.invalid.json`, the report aborts with exit 3 and a loud message, and invalid snapshots are excluded from diffs.
- **Invalidation:** `measurements/2026-09-07.json` → `2026-09-07.invalid.json` with `invalid: true` and reason recorded; content preserved.
- **Re-run 2026-09-11 (valid):** **3/10** — `eGEOagents` ✅, `eGEOagents GitHub` ✅, `GEO evaluation harness open source` ✅; head query ❌; no change vs 2026-08-31. Gate A remains unmet.

## 4. Findings and prioritized fixes

| Pri | Finding | Proposed fix |
|---|---|---|
| **P0** | PyPI package cannot run core workflows (missing `prompts/`, `collectors/`, `SUBSTRATE.md`, `examples/`) | Move resources into the `egeo` package (or add `package-data` + path resolution that falls back to package resources), add a CI step that installs the built wheel in a clean venv and runs `optimize`/`evaluate`/`loop doctor` smoke checks, then cut a patch release |
| **P1** | Docs/llms.txt advertise `pip install egeo` while the wheel is broken | After the P0 fix ships, no doc change needed; until then the site/README overpromise the PyPI path |
| **P1** | `egeo runtimes` on the wheel reports the `python` runtime "unavailable" | Same root cause as P0 (resource import chain); verify after fix |
| **P2** | Mock evaluate reports perfect scores (`win_rate 1.0`) by construction | Keep as contract test; never cite as effectiveness evidence (per deferred scientific review recorded in the roadmap proposal) |
| **P2** | OpenSpec shipped changes not archived; no `openspec/specs/` | Housekeeping PR: archive `add-geo-loop`, `add-portable-project-config`, `add-loop-decision-layer`, `add-runtime-adapters` after confirming each against the code |

## 5. Scope notes

- No code was changed in this repository in this phase. The only edits were to the marketing measurement script and its snapshot archive (outside the repo).
- The Reddit engine 403-retry loop observed earlier is an operational issue in `~/...` tooling, out of scope for this baseline; it is tracked in the marketing tree.
- Wheel first-use was also exercised with a pre-existing `EGEO_HOME`; the clean-home failures above are the representative new-user path.

## Gate B

Requesting owner review of this baseline. Proposed next step: implement the P0 packaging fix as a small PR with a wheel-smoke CI job, then decide the patch release. No feature work starts before this review.
