# TASK: Rebuild the egeoagents.com landing from zero — studio-quality, cinematic, dev-tool

BUILD NOW in the repo at cwd (auto-branch from main is active). No web search. No questions.

CONTEXT: a previous landing attempt (plain Starlight-style page) was REJECTED by the owner as far below the quality bar. The reference bar is a cinematic, editorial, motion-rich hero: GSAP word-by-word reveals, native GLSL shader layers, film grain, magnetic CTAs, one accent color on warm black, generous whitespace. That reference was for a personal brand; adapt every creative choice to THIS product: E-GEO, an open-source GEO/AEO CLI toolkit for developers. Language: English.

## Product facts (verified, use only these)

- E-GEO — open-source Generative Engine Optimization (GEO) & Answer Engine Optimization (AEO) toolkit (Python CLI + Claude Code skills), based on published GEO research (arXiv:2511.20867). MIT. 147 stars, 42 forks (as of 2026-08).
- CLI: `pip install egeo` → `egeo optimize content.md` (subcommands: optimize, evaluate, optimize-prompts, runtimes, loop). Also `npx skills add https://github.com/mverab/eGEOagents`.
- Differentiators: reproducible evaluation harness (offline, GEO_EVAL_MOCK=1), continuous geo-loop mode, full analyze→rank-simulate→rewrite→schema pipeline, MCP-based validation layer, schema generator.
- Read egeo/cli.py and geo-output/ + examples/ for realistic terminal output.

## Creative spec (adapted from the owner's reference guideline)

**Aesthetic:** warm black base (#0B0B0B), bone white text (#F5F1EA), ONE accent (amber #E8A857 or argue a better one — document the choice). Film grain overlay (subtle ~8%). Editorial typography: a serif display (Fraunces via fontsource or system fallback stack) for the headline + Inter for body + JetBrains Mono for labels/terminal. Forbidden: neon, cyan glow, circuit boards, generic gradient blobs, centered corporate SaaS layout, emoji.

**Hero (100vh, left-aligned, 8vw padding):**
1. Micro-label mono uppercase amber: `◆ open-source geo/aeo toolkit` — fades in first.
2. Headline (GSAP word-by-word: blur 20px→0, y 40px→0, 0.08s stagger): something like "rank where people actually search." — you write it; direct, anti-hype, dev-literate. Accent-shift one word to amber.
3. Subtitle: what it does in one honest sentence (analyzes, scores, rewrites your content so ChatGPT, Perplexity, Gemini & Claude cite it).
4. **Terminal demo** — the centerpiece, right side or below depending on viewport: realistic typed animation (pip install egeo → egeo optimize → pipeline stages → score 42→87 with per-feature checkmarks). Hand-rolled JS typing engine, crisp timing, blinking cursor, clean end state (loops only if seamless). Real DOM text, selectable.
5. CTAs: primary `get started →` (/docs/getting-started/), secondary ghost `★ star on github` (repo URL), tertiary text link `read the paper ↗` (arXiv). Magnetic hover on primary, underline-grow on links.
6. Bottom strip, mono, 40% opacity: `147★ · 42 forks · mit licensed · arxiv:2511.20867` — fades in last.

**Shader layer:** ONE subtle WebGL/GLSL background effect behind the hero (e.g. slow ink-bleed/fluid SDF or fine noise-drift), throttled rAF, paused on tab blur, disabled under prefers-reduced-motion, graceful static fallback if WebGL missing. No Three.js needed unless you justify it; keep the bundle lean.

**Sections after hero (keep tight, editorial):** how it works (3 steps: analyze → rewrite → measure, with real command snippets) → features (4-6 cards, real capabilities only) → honest dated comparison table (reuse data from site/src/content/docs/compare/geo-tools-2026.md, "Last verified: 2026-08-05") → install (both paths, copy buttons) → final CTA → footer (GitHub, arXiv, docs).

**Hard SEO/GEO requirements (non-negotiable, carried from current site):**
- SoftwareApplication JSON-LD on / (same fields as the current build: MIT license, codeRepository, citation arXiv:2511.20867, offers price 0, author Person Miguel Vera sameAs github.com/mverab) + keep global Organization JSON-LD.
- Canonical entity sentence verbatim, visible in HTML: "E-GEO — open-source Generative Engine Optimization (GEO) & Answer Engine Optimization (AEO) toolkit (Python CLI + Claude Code skills), based on published GEO research (arXiv:2511.20867)."
- Answer block 50-170 words as real HTML text (crawlable, not in canvas).
- All internal links to existing routes (/docs/getting-started/, /docs/cli/, /docs/faq/, /concepts/what-is-geo/, /compare/*).

## Technical

- Replace whatever currently serves `/` (the rejected attempt removed the Starlight splash; check git: main still has site/src/content/docs/index.mdx — remove it and serve a custom Astro page, e.g. src/pages/index.astro). Starlight continues serving /docs/*, /concepts/*, /compare/* untouched. Fix sidebar config if it referenced the splash.
- Vanilla Astro + GSAP (npm) allowed. No React/Next. Static output. Landing total weight target < 400KB (fonts subset, GSAP is fine).
- Responsive 375/768/1440. prefers-reduced-motion → static final states. Lighthouse 90+ desktop.
- Extend site/verify.sh: keep all existing checks + assert: JSON-LD, entity sentence, answer block, terminal element, sitemap includes /. `npm run build` + `bash verify.sh` must pass — show output.

## Finish

Conventional commits on your branch. End with: branch name, commit hashes, verify output summary, accent color chosen, GSAP version.
