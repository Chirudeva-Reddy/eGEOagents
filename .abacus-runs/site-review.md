# Pre-merge review — feat/starlight-site (E-GEO docs site)

Reviewer: independent, adversarial, read-only. Date: 2026-08-05. Branch: `feat/starlight-site` (2 commits vs `main`: d1eaccf, bc4f879). All commands re-run locally; nothing taken on trust.

## 1. Factual accuracy vs repo

- `pyproject.toml` `[project.scripts]`: `egeo = "egeo.cli:main"` — matches site's `pip install -e .` / `python -m egeo` instructions (README.md:253-257 says the same).
- `python -m egeo --help` (exit 0, `egeo 2.0.0`): subcommands `{optimize,evaluate,optimize-prompts,runtimes,loop}` — exactly the set documented in `site/src/content/docs/docs/cli.md`.
- Per-subcommand `--help` compared line-by-line against cli.md:
  - `optimize`: usage block, all flags (`--out-dir`, `--query`, `--schema-type {Organization,Product,Service,Article,FAQPage}`, `--runtime`, `--ranker-model`, `--rewriter-model`, `--temperature`, `--json`) and defaults (`geo-output`, `Article`, `python`) match real help output. **No invented flags.**
  - `evaluate`: `--dataset` (required), `--prompts`, `--ranker-model`, `--rewriter-model`, `--temperature`, `--seed`, `--limit`, `--verbose` — all match.
  - `optimize-prompts`: `--train`, `--val`, `--prompts`, `--meta-model`, `--iters`, `--apply` (non-destructive default `*.candidate.txt`) — all match.
  - `runtimes`: `--json` — matches. Runtime table (`python` aliases `cli,local`; `claude-code` alias `claude`) consistent with `egeo/runtimes.py` docs claim.
  - `loop`: `{run,collect,doctor}`; `run --dry-run --json`, `collect {page,serp}` with forwarded `--fixture/--json/--query/--url`, `doctor --json` — all match real help. `--target-domain` (cli.md:135) verified real: `collectors/serp.py:207`.
- Documented example commands executed for real:
  - `GEO_EVAL_MOCK=1 python -m egeo evaluate --dataset eval/datasets/geo_smoke.jsonl --limit 2` → exit 0.
  - `GEO_EVAL_MOCK=1 python -m egeo optimize examples/sample-input.md --out-dir /tmp/egeo-test` → exit 0; wrote `report.md`, `analysis.json`, `optimized/`, `schema/` — but **no `checklist.md`** (see Issue 3).
  - `python -c "import egeo.substrate_lint"` → OK (geo-loop.md:37 claim holds); `SUBSTRATE.md` exists.
  - `examples/sample-input.md` and `eval/datasets/geo_smoke.jsonl` exist as referenced.
- Skills: `.claude/skills/` contains exactly `competitive-analysis`, `content-scoring`, `geo-loop`, `schema-generator`, `validation-doctor` — all five listed by the site exist. `.claude/agents/` (geo-analyzer/ranker/rewriter/indexer) and `.claude/output-styles/geo-optimizer.md` exist, so `/output-style geo-optimizer` and the 4-agent table in getting-started.md are traceable.
- "Same check runs in CI": `.github/workflows/ci.yml:71,81` sets `GEO_EVAL_MOCK: "1"` — claim holds.
- **Fails**: the "(Python CLI + MCP server)" positioning and the CLI `checklist.md` claim — see Issues 1 and 3.

## 2. Comparison honesty

- geo-optimizer-skill credited with **~617 stars** (index.mdx:90, compare/e-geo-vs-geo-optimizer-skill.md:35,45, compare/geo-tools-2026.md:35, faq.md:16,51) and **47 scoring methods** (same pages) — required credits present everywhere.
- Live check (web, 2026-08-05): competitor repo shows **644 stars**; "~617 as of 2026-08" is already low in the very month it claims (Issue 5). E-GEO "147 stars" vs 148 live — fine.
- Differentiators claimed: rewriting pipeline (traceable to README.md:416 "Content Rewriting: Full pipeline"), reproducible evaluation harness (README/eval/, verified runnable), geo-loop (verified runnable), arXiv:2511.20867 (README.md:18,56,196…), Claude Code skills distribution (README.md:136-159, skills exist). "Rewriting" is a fifth differentiator beyond the allowed four (Issue 4).
- Claims about the competitor ("audit-focused", "no reproducible evaluation harness or continuous mode", geo-tools-2026.md:52) mirror README.md:415-424 but are not independently verified against the competitor's repo — inherited risk, not introduced by this branch.
- "MCP server" attributed to **E-GEO itself** contradicts the repo (Issue 1 — blocker).

## 3. Schema validity (built dist)

Extracted every `<script type="application/ld+json">` from `site/dist/**/*.html` and parsed with `json.loads` — **all 27 blocks parse; zero malformed JSON**. Placement:

| Page | Types found |
|---|---|
| `dist/index.html` | Organization, **SoftwareApplication** ✓ (landing only — no other page has it) |
| `dist/docs/{cli,evaluation,geo-loop,getting-started,how-it-works,mcp-server}` | Organization, TechArticle ✓ |
| `dist/docs/faq`, `dist/concepts/{what-is-geo,what-is-aeo,geo-vs-seo}` | Organization, FAQPage ✓ |
| `dist/compare/*` | Organization, Article (with `mainEntity` ItemList in source) ✓ |
| `dist/404.html` | Organization only |

The site-wide `Organization` block is injected globally via `astro.config.mjs:39-45` — acceptable publisher markup, not a placement violation. SoftwareApplication `description` embeds the false "MCP server" claim (Issue 1).

## 4. Build integrity (re-run, not trusted)

- `rm -rf dist && npm run build` → **exit 0**, 14 pages, sitemap + Pagefind index generated.
- `bash verify.sh` → **exit 0**, all 11 checks PASS.
- `npm ci --dry-run` → **exit 0** (lockfile in sync with package.json); local node v22.22.3 matches workflow's node 22.

## 5. Routes and links

Route map from built dist (13 routes) cross-checked against every internal `](/...)` link in `src/content/**/*.md*` via script: **0 dead internal links**. All sidebar slugs in `astro.config.mjs:46-79` correspond to existing content files (build would have failed otherwise; it didn't).

## 6. llms.txt spec

`site/public/llms.txt`: H1 (`# E-GEO`) → blockquote summary → prose paragraph → `## Docs` / `## Concepts` / `## Compare` / `## Optional` sections of `- [name](url): description` links. Conforms to llmstxt.org. All 12 site links are absolute `https://egeoagents.com/...`; zero `http://` links in either file. `llms-full.txt` (H1 + blockquote + sections) also well-formed. Both repeat the "MCP server" claim at line 3 (Issue 1) and "peer-reviewed" (Issue 2).

## 7. Workflow (.github/workflows/site.yml)

- `yaml.safe_load` → parses clean.
- Triggers: push + pull_request filtered to `site/**` and the workflow file itself — builds only on site changes ✓.
- `defaults.run.working-directory: site` ✓; `actions/setup-node@v4` node 22, npm cache keyed on `site/package-lock.json` ✓.
- `site/package-lock.json` **is committed** (6765 lines in diff), so `npm ci` will work; verified via `npm ci --dry-run` exit 0.
- `- run: ./verify.sh` requires the executable bit: `git ls-files -s site/verify.sh` → mode **100755** ✓.
- Steps are `npm ci` + `npm run build` + `verify.sh` as required. Nothing CI-breaking found. (Note: workflow builds/verifies only; there is no deploy step — egeoagents.com is not published by this workflow.)

## 8. Placeholders

`grep -rni "TODO|lorem|FIXME|placeholder|example\.com" site/src site/public`: no TODO/FIXME/lorem/placeholder. `example.com` appears only inside illustrative CLI/schema code examples (cli.md:135-136, geo-loop.md:60-61,93, how-it-works.md:49) — legitimate use of the reserved example domain, not an unfilled placeholder.

## 9. Repo hygiene

`git diff main...feat/starlight-site --stat`: 29 files, all under `site/` plus `.github/workflows/site.yml`. **Zero changes** to the original `docs/`, `egeo/`, `README.md`, or anything else. Working tree clean except untracked `.abacus-runs/` (this review's own output dir).

---

## VERDICT: ISSUES

1. **[blocker] E-GEO is repeatedly described as "(Python CLI + MCP server)" — the repo contains no MCP server.** Grep of the repo finds no MCP server implementation; the repo's own comparison table (README.md:415) lists E-GEO as "CLI + Claude Code" and credits the *competitor* with "CLI + MCP"; the site's own `docs/mcp-server.md` correctly describes E-GEO as an MCP *client* (it consumes brave-search/chrome-devtools servers). Yet the site's canonical description claims E-GEO ships an MCP server, in: `site/astro.config.mjs:28` (global site description), `site/src/content/docs/index.mdx:3,25,49` (including the SoftwareApplication JSON-LD emitted on the landing page), `site/public/llms.txt:3`, `site/public/llms-full.txt:3`, `site/src/content/docs/compare/geo-tools-2026.md:36,48`. For a project whose comparison pages stake everything on honesty, shipping a false capability claim in the schema and llms.txt is disqualifying as-is. Fix: "(Python CLI + Claude Code skills)" or "with MCP-based validation".
2. **[minor] "Peer-reviewed paper/research" for an arXiv preprint** (index.mdx:83,95; faq.md:16,36,58; both compare pages; both llms files; astro.config.mjs:28). arXiv posting is not peer review. The claim is traceable to the repo (README.md:56,59,196 makes it too), so it's inherited rather than invented — but the site amplifies it into FAQPage JSON-LD and llms.txt. Recommend "research paper (arXiv:2511.20867)" unless a peer-reviewed venue acceptance can be cited.
3. **[minor] `checklist.md` falsely attributed to the CLI path.** `site/src/content/docs/docs/getting-started.md:88-97` says "Both paths write a complete optimization package … └── checklist.md". Verified: `GEO_EVAL_MOCK=1 egeo optimize` writes only `report.md`, `analysis.json`, `optimized/`, `schema/`; `grep checklist egeo/*.py` → no matches. Only the Claude Code agent path produces a checklist. Reword or scope to the agent workflow.
4. **[minor] Differentiator list exceeds the agreed four.** The review contract limits E-GEO differentiators to: evaluation harness, geo-loop, arXiv paper, skills distribution. "It rewrites, not just scores" is presented as differentiator #1 in `compare/e-geo-vs-geo-optimizer-skill.md:51`, `docs/faq.md:57`, and `index.mdx:95`. It is repo-traceable (README.md:416 claims full-pipeline rewriting, verified working) but rests on the unverified premise that the competitor doesn't rewrite; same for the absolute claim "No other open-source GEO tool ships an equivalent [harness]" (`compare/e-geo-vs-geo-optimizer-skill.md:52`). Either verify against the competitor's current repo or soften.
5. **[minor] Competitor star count already stale.** Pages dated "Last verified: 2026-08-05" say "~617 stars as of 2026-08"; the competitor repo shows **644** as of that same date (web-checked 2026-08-05). Understating a competitor by ~4% on a page that advertises its own honesty invites exactly the criticism it disclaims. Update to ~644 (E-GEO's 147→148 is within tolerance).
6. **[minor] Competitor links point to the org, not the repo.** `https://github.com/Auriti-Labs` (org page) instead of `https://github.com/Auriti-Labs/geo-optimizer-skill` in `compare/e-geo-vs-geo-optimizer-skill.md:23` (JSON-LD ItemList url) and :33, `compare/geo-tools-2026.md:22,35`, `docs/faq.md:51`. The ItemList entry's `url` should identify the item itself.

Blocker #1 must be fixed before merge; #2–#6 are strongly recommended. Build, schema JSON, routes, llms.txt structure, workflow, and repo hygiene all pass.
