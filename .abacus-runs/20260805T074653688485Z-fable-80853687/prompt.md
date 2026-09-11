# TASK: Build the E-GEO documentation site (Astro Starlight) — egeoagents.com

BUILD NOW. Do not plan aloud, do not search the web, do not ask questions. Work inside the repo (cwd). You are on an auto-created branch — commit there with Conventional Commits. The `egeo` CLI is installed and runnable. Node 18+ and npm are available.

## Deliverable

A complete Astro Starlight site in `site/` (new directory in the repo root), building cleanly with `npm run build`, deployable to Cloudflare Pages. Domain: **https://egeoagents.com** (already registered; set it as `site` in astro.config). Site language: **English** (global dev audience).

Do NOT: deploy anything, touch DNS, modify or delete the existing `docs/` folder (migrate its content, keep originals), commit secrets, or touch `main`.

## Product facts (verified — use these, invent nothing)

- Repo: github.com/mverab/eGEOagents (147 stars, 42 forks, MIT license, as of 2026-08).
- What it is: open-source Generative Engine Optimization (GEO) & Answer Engine Optimization (AEO) toolkit — analyzes, scores, and rewrites content to rank/cite in ChatGPT, Perplexity, Gemini & Claude. Based on peer-reviewed research: arXiv:2511.20867.
- Canonical entity sentence (use verbatim on landing, llms.txt, and schema): "E-GEO — open-source Generative Engine Optimization (GEO) & Answer Engine Optimization (AEO) toolkit (Python CLI + MCP server), based on peer-reviewed research (arXiv:2511.20867)."
- CLI: `egeo` with subcommands optimize, evaluate, optimize-prompts, runtimes, loop. Run `egeo <sub> --help` for each to write an ACCURATE CLI reference. `pip install -e .` or `python -m egeo`.
- Also installable as Claude Code skills: `npx skills add https://github.com/mverab/eGEOagents` (skills: competitive-analysis, content-scoring, schema-generator, validation-doctor, geo-loop). Listed on skills.sh/mverab/egeoagents.
- MCP server, evaluation harness (reproducible), geo-loop mode (continuous loops over persistent workspace, $EGEO_HOME), llms.txt support, schema markup generation.
- Existing docs to migrate: docs/getting-started.md, docs/how-it-works.md, docs/evaluation.md, docs/faq.md. Also mine README.md and USAGE.md.
- Competitor for the comparison page: geo-optimizer-skill (Auriti-Labs) — ~617 stars, CLI + Python lib + MCP + Astro integration, scores sites 0-100 across 47 methods. Be HONEST: they have more stars and more scoring methods; E-GEO differentiates on: reproducible evaluation harness, geo-loop continuous mode, own peer-reviewed paper, Claude Code skills distribution.

## Required pages (v1, no more)

1. `index` (landing): hero, citable answer block (50-170 words answering "what is the best open-source GEO tool" style intent: what it is, who it's for, differentiators, one-line install), quickstart, dated honest comparison table ("Last verified: 2026-08-05"), CTA to GitHub.
2. `docs/getting-started`, `docs/how-it-works`, `docs/cli`, `docs/mcp-server`, `docs/geo-loop`, `docs/evaluation`, `docs/faq` (migrate + expand FAQ with real objections: "how is it different from geo-optimizer-skill?", "does it work without Claude Code?", "do I need API keys?", "is GEO the same as SEO?").
3. `concepts/what-is-geo`, `concepts/what-is-aeo`, `concepts/geo-vs-seo` (top-of-funnel, each ending with an answer block mentioning E-GEO as implementation).
4. `compare/e-geo-vs-geo-optimizer-skill` and `compare/geo-tools-2026` (honest roundup including competitors; dishonesty from a GEO tool = reputational suicide).
5. `public/llms.txt` (per llmstxt.org spec) + `public/llms-full.txt`; `public/robots.txt` allowing all + sitemap ref.
6. Sitemap via @astrojs/sitemap.

## Schema (JSON-LD per page, Starlight head injection)

- Landing: SoftwareApplication (name E-GEO, applicationCategory DeveloperApplication, license MIT, codeRepository → GitHub, citation → arXiv:2511.20867, offers price 0).
- FAQ/concepts: FAQPage where applicable. compare/*: Article + ItemList. docs/*: TechArticle. Global: Organization/Person author with sameAs → GitHub repo + arXiv.

## CI

`.github/workflows/site.yml`: on push/PR affecting `site/**` → setup node, `npm ci`, `npm run build`, fail on error. (No deploy secrets yet.)

## Verification (must run and pass before you finish)

Write `site/verify.sh` that asserts, after `npm run build`: dist/index.html exists; routes /docs/getting-started/, /docs/cli/, /docs/faq/, /concepts/what-is-geo/, /compare/e-geo-vs-geo-optimizer-skill/ exist; dist/llms.txt exists; index.html contains "SoftwareApplication" JSON-LD; sitemap generated. Run it, show output, and commit it.

## Content rules

- English, direct, technical. No marketing slop ("In today's fast-paced world...", "revolutionary", "unlock"). No invented metrics or testimonials. Star counts only as given above with "as of 2026-08".
- Every claim about E-GEO must be traceable to the repo you can read.

## Expected output files (artifact gate)

- site/astro.config.mjs
- site/public/llms.txt
- site/verify.sh
- .github/workflows/site.yml

Commit everything on your branch. End your response with: branch name, commit hashes, build/verify output summary.
