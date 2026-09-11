# TASK: Custom cinematic landing page for egeoagents.com (terminal-native, anti-image hero)

BUILD NOW in the repo at cwd (auto-branch is active). No web search. No questions. Read the existing site first: site/astro.config.mjs, site/src/content/docs/index.mdx (current Starlight splash at /), site/verify.sh.

## Goal

Replace the default Starlight splash homepage with a custom, designed landing page at `/` — dev-tool aesthetic in the lineage of vercel.com and turbo.build: near-black background, one accent color (you choose, document it), crisp type scale, generous whitespace. Starlight keeps serving /docs/*, /concepts/*, /compare/* exactly as today.

## Hero: terminal-native (NO generated images, NO video)

The hero centerpiece is a **self-playing terminal demo** (pure HTML/CSS/JS, typed animation): shows `pip install egeo` → `egeo optimize content.md` → realistic scored output (e.g. GEO score 42/100 → 87/100, the pipeline stages analyze → rank-simulate → rewrite → schema appearing step by step). The demo content must be traceable to real CLI behavior — read egeo/cli.py and geo-output/ examples in the repo. Terminal must be a real DOM element with monospace font, not a canvas/image. Ambient, subtle, loops cleanly or ends static. No zoom drift, no layout shift.

## Hard requirements (carry over from current landing — SEO/GEO integrity)

1. **SoftwareApplication JSON-LD** on / (same data as current index.mdx: license MIT, codeRepository, citation arXiv:2511.20867, offers price 0, author Person Miguel Vera sameAs github.com/mverab). Keep the global Organization JSON-LD working.
2. **Canonical entity sentence verbatim somewhere visible:** "E-GEO — open-source Generative Engine Optimization (GEO) & Answer Engine Optimization (AEO) toolkit (Python CLI + Claude Code skills), based on published GEO research (arXiv:2511.20867)."
3. **Citable answer block** (50-170 words, real HTML text): what it is, who for, differentiators (reproducible evaluation harness offline with GEO_EVAL_MOCK=1, geo-loop continuous mode, research basis, Claude Code skills), one-line install.
4. **Honest dated comparison table** (reuse data from compare/geo-tools-2026.md, "Last verified: 2026-08-05").
5. Sections: hero → answer block → how it works (3 steps) → features (4-6 cards: CLI, eval harness, geo-loop, MCP validation, schema generator, skills distribution) → comparison table → install (both paths: pip install egeo AND npx skills add) → CTA GitHub → footer (GitHub, arXiv paper, docs links).
6. Language: English. No marketing slop. No invented metrics. Stars "147 as of 2026-08" is the only stat allowed.
7. Internal links must point to the real existing routes (/docs/getting-started/, /docs/cli/, /docs/faq/, /concepts/what-is-geo/, /compare/*). External: https://github.com/mverab/eGEOagents, https://arxiv.org/abs/2511.20867.

## Technical constraints

- Astro static output. Implement the custom landing as a standalone page (e.g. src/pages/index.astro) and REMOVE the Starlight splash (site/src/content/docs/index.mdx) so routes don't collide; the docs sidebar must not break (update astro.config.mjs sidebar if it linked the splash). /docs/getting-started/ remains the docs entry.
- Custom CSS scoped to the landing (no Tailwind install; hand-rolled CSS or Astro scoped styles). No new heavy dependencies. Page weight target < 150KB total for /.
- Responsive: verified at 375 / 768 / 1440px (no overflow, terminal readable at 375).
- Accessibility: semantic landmarks, contrast AA, prefers-reduced-motion disables the terminal animation (static final frame).
- sitemap must still include / (verify dist/sitemap-0.xml).
- Extend site/verify.sh: / builds, SoftwareApplication JSON-LD present, answer block text present, terminal hero element present, no link to /docs/index remnants. All previous checks must still pass.
- `npm run build` + `bash verify.sh` must pass — run them and show output.
- Update public/llms.txt ONLY if the landing's visible content changed materially (it should not — keep links intact).

## Content rules

Factual, English, direct. No "revolutionary/seamless/unlock". Claims traceable to the repo.

## Finish

Conventional commits on your branch. End with: branch name, commit hashes, build/verify summary, and the chosen accent color.
