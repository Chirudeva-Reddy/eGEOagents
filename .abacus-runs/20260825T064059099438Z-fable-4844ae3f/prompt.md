WRITE NOW. Do not search. Do not plan. Use your file() tool.

Write the full verdict document to exactly:
/home/hermes-2/Sync/mkt/egeo-expansion/2026-08-25-dsh-plugin-viability.md

Language: Spanish mexicano, informal tuteo, sin voseo. Repo/code names stay in English.
Do NOT edit any git repo. Do NOT write code. Do NOT invent stars, URLs, measurements, or file paths.

# Output contract (mandatory sections, in this order)

1. **Dictamen** — one line: `NO VIABLE` | `VIABLE-CONDICIONAL` | `VIABLE` plus a 1-sentence reason.
2. **Qué se evaluó** — the idea in one paragraph.
3. **Evidencia** — table: fact | source in this brief | implication.
4. **Por qué sí / por qué no** — max 6 bullets, each with a causal mechanism.
5. **Vs plan ya vigente** — compare this idea against the already-planned next steps. Name the conflict or complementarity.
6. **Recomendación única** — ONE next step. If DSH is not that step, name the alternative that already exists in OpenSpec/expansion plan and why it wins now.
7. **Si más tarde** — the cheapest DSH shape that would become viable later, and the gate that unlocks it.
8. **Open decisions** — exactly 2, each with YOUR recommendation.

Hard rules:
- Treat official DSH "developer preview + breaking changes" as a first-class risk, not a footnote.
- Do not recommend rewriting the Python CLI as a Cordis/TypeScript product.
- Do not recommend open-core or a second product.
- Gate A in the expansion plan is ≥3/10 Perplexity mentions OR ≥300⭐. Current live numbers are in Evidence below — do not flip-flop the monetization sequence.
- End with: `Siguiente gate: <one owner decision in one sentence>`.

# Distilled idea

Owner question: eGEOagents already has a real GEO product (CLI `egeo` + Claude Code skills + loop). DeepSeek Harness (DSH) just exploded as a plugin ecosystem. Owner reviewed plugin-compiler / bridge projects. Should we add a DSH plugin (or compile the existing Claude/CLI surface into DSH) inside the eGEOagents repo as the next scale step?

# Evidence (verified 2026-08-25 by Hermes — treat as ground truth)

## DSH + market
- `deepseek-ai/deepseek-harness`: 193,130⭐, TypeScript, MIT, developer preview. Official warning: THERE WILL BE COMPATIBILITY-BREAKING CHANGES. Philosophy: everything is a Cordis plugin (models, tools, skills, sessions, sandbox, storage, loops, scheduling, UI). No privileged core.
- Plugin contract: npm package with `package.json` → `dsh.bundle.patch` pointing at `cordis.patch.yml`. Install: `dsh plugin --profile web add <pkg|github:owner/repo>`. Profiles (`web`, `headless`) stack bundles; later patches replace whole config rows by id.
- Official docs: https://deepseek-harness.github.io/deepseek-harness/en/guide/quickstart and architecture.md. Launch: `npx @deepseek-ai/dsh web` → http://127.0.0.1:3080.
- `dsh-market/dsh-market`: 2,255⭐, TS, pushed 2026-08-25. In-UI Plugin Market. Catalog is NOT this repo — it consumes curated `awesome-dsh-plugin` / plugins.json. Listing a plugin = PR to the catalog, not a PR to dsh-market. 1550+ community plugins claimed; competing markets exist (NanmiCoder 3518 catalog entries, sandbaseai 4000+). High noise.
- Plugin authoring is TypeScript + Cordis (`export function apply(ctx)`, `inject`, reversible `ctx.effect`). Skills can also be dropped as `SKILL.md` dirs, but updates then are copy-paste unless wrapped as a bundle.

## Plugin compilers / bridges (the architecture the owner reviewed)
- `openma-ai/dsh-agents-plugins` (2⭐): Bridge kernel. Detects foreign formats (Claude Code plugins, Codex plugins, Pi packages), copies a selected package into profile-local storage, materializes each capability as its own reversible DSH row. Does NOT emulate another runtime. Install `@openma/dsh-agents-plugins-bridge`. Web: Settings → Plugins → Agent plugins.
- `leechen298/Code2Skill` (8⭐): generates Functions + MCP + Skills from existing authorized source. Not a DSH-native compiler of the egeo CLI; a skill pack that can be installed INTO DSH.
- `YYTbit/dsh-plugin-claude-bridge` (9⭐): bring Claude Code memory/skills/config into DSH.
- Pattern: compilers wrap existing agent packages; they do not port a Python product into Cordis.

## eGEOagents current state (canonical clone `~/workspace/projects/github/mverab/eGEOagents`)
- Public: `mverab/eGEOagents`, 164⭐, 45 forks, homepage https://egeoagents.com, PyPI package `egeo` = 404 (not published). Version 2.0.0.
- Surfaces that exist: Claude Code (`.claude/agents|commands|skills`), standalone Python CLI (`egeo optimize|evaluate|optimize-prompts|runtimes|loop`), loop mode (`egeo loop run|collect|doctor`) over `$EGEO_HOME` (default `~/.egeo`).
- Runtime adapter layer (`egeo/runtimes.py`): only `python` (in-process) and `claude-code` (descriptor). Design explicitly rejected a plugin/entry-point system as premature. Deferred: cursor/windsurf descriptors; `--competitors` flag.
- Active OpenSpec change (implemented, on `feat/portable-project-contract`, tasks 1–4 checked): `add-portable-project-config` — `$EGEO_HOME/project.yaml` so a second project is data, not code. This is the unfinished scale step already in flight.
- Older OpenSpec (already implemented in v2): `add-runtime-adapters`, `add-geo-loop`, `harden-quality-and-expose-eval`, `add-skills-sh-discoverability`, `launch-opensource-geo`.
- Three-product framing (owner-normative, do not reframe): LoopStack = loop system; eGEOagents = product being scaled; SlashStack = PoC workload. Learnings feed back; do not fork a fourth product.
- Constraints: MIT, honesty (no fabricated proof), human-reviewed apply, no open-core, CLI stays 100% free.

## Planned scale path already on record (2026-08-05 Fable strategy, still governing)
File: `~/Sync/mkt/egeo-expansion/2026-08-05-analisis-visibilidad-y-expansion.md`
- Diagnosis: on-repo SEO does not move answer-engine rank. Citability comes from LibHunt, awesome-lists, own site, third-party articles.
- Monetization sequence: services now → Gate A (≥3/10 mentions OR ≥300⭐) course → Gate B (≥500⭐ or ≥20 WTP) hosted geo-loop SaaS. Open core vetoed.
- 30/60/90: site + backlinks + measurement + PyPI + case study. Not "new harness integration".
- Live progress: site egeoagents.com exists; LibHunt listed; skills.sh live; awesome-list issue #99 + izak-fisher PR #46 still pending; PyPI unpublished.
- Perplexity measurement (`egeo_mentioned`): 2026-08-11 = 3/10; 2026-08-17 = 4/10; 2026-08-24 = 3/10. Hits are almost all branded (`eGEOagents`, `eGEOagents GitHub`) plus "GEO evaluation harness open source". Category head query still false. Stars 164 < 300.

## Fit analysis seeds (you must accept or refute with mechanism)
- A native Cordis rewrite of the 4-agent pipeline = new TS stack + unstable DSH APIs + duplicated product. High cost, low GEO-citability return.
- A thin DSH bundle that registers `/geo` skills and shells out to the existing `egeo` CLI = cheap distribution adapter, same as the already-planned cursor/windsurf descriptors.
- Using `dsh-agents-plugins` to import `.claude/` as-is = cheapest experiment, lives outside the eGEOagents repo, does not scale the product.
- DSH market listing helps DSH-user discovery, not Perplexity/ChatGPT citations. Different distribution surface than the governing plan.
- WIP that already scales the product: finish/merge `project.yaml`, publish PyPI, close pending backlinks, produce the 6-week case study.

Recommend one path. If you mark VIABLE-CONDICIONAL, the condition must be a gate with a number, not a vibe.
