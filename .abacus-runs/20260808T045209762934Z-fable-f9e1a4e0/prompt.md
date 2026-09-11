# TASK: Build the FULL egeoagents.com landing in the swiss/brutalist direction you just designed

The owner picked variant C (swiss). Now implement it as the real landing page of the Astro site in this repo. You are on branch chore/design-variants — continue on it. The seed is design-variants/c-swiss.html: extend its language (white, black, Archivo grotesk, hard 2px grid rules, one fluorescent chartreuse #D4FF00 used sparingly) into a complete page. Keep design-variants/ files as-is (they're reference, Astro doesn't build them).

## Build target

- Replace the current `/` (Starlight splash at site/src/content/docs/index.mdx — remove it) with a custom Astro page site/src/pages/index.astro. Starlight keeps serving /docs/*, /concepts/*, /compare/* untouched. Fix site/astro.config.mjs sidebar if it referenced the splash.
- Static, vanilla Astro. Keep total landing weight < 400KB. Fonts: Archivo via fontsource or Google Fonts with preconnect + font-display swap, subset.
- Responsive 375/768/1440. prefers-reduced-motion → static final states. Semantic landmarks, AA contrast (chartreuse on white fails AA for text — use it only for large graphic elements/underlines/marks, never body text).

## Motion (tasteful, swiss = restraint)

- Headline reveal: GSAP word-by-word (y 40→0, blur 20→0, 0.06s stagger) is allowed; keep everything else to hard-edged, grid-snapped transitions (line draws, block wipes). No floating blobs, no parallax circus.
- The answer-card hero visual from your variant: keep it, refine it. It must read as the web/AI-answer moment, not a dev tool. Absolutely no terminal/shell/code-block aesthetics anywhere. Install commands only as small copy-chips in the install section.

## Content (approved copy from the variants; expand sections)

Hero: micro-label (sparingly — swiss doesn't need mono clichés; a plain small caps label is fine), headline "your customers stopped searching. they started asking." (improve only if clearly better), sub about analyze/rewrite/schema so ChatGPT/Perplexity/Gemini/Claude cite you, CTAs: primary `get started →` (/docs/getting-started/), ghost `★ star on github` (https://github.com/mverab/eGEOagents), text `read the research ↗` (https://arxiv.org/abs/2511.20867). Bottom strip: `147★ · 42 forks · mit · arxiv:2511.20867`.

Sections: the shift (answer engines are the new front page — 2-3 editorial sentences) → how it works (3 steps in plain words: analyze → rewrite → get cited; NO code) → capabilities grid (10-feature GEO scoring, content rewriting, JSON-LD schema generation, reproducible evaluation harness, continuous monitoring loop, Claude Code skills) → honest dated comparison table (data from site/src/content/docs/compare/geo-tools-2026.md, "Last verified: 2026-08-05") → install (two copy-chips: pip install egeo / npx skills add https://github.com/mverab/eGEOagents) → final CTA → footer.

## Hard SEO/GEO requirements (non-negotiable)

- SoftwareApplication JSON-LD on / (MIT, codeRepository https://github.com/mverab/eGEOagents, citation arXiv:2511.20867, offers price 0, author Person Miguel Vera sameAs github.com/mverab) + global Organization JSON-LD preserved.
- Canonical entity sentence verbatim, visible HTML: "E-GEO — open-source Generative Engine Optimization (GEO) & Answer Engine Optimization (AEO) toolkit (Python CLI + Claude Code skills), based on published GEO research (arXiv:2511.20867)."
- Answer block 50-170 words as crawlable HTML text.
- All internal links to real existing routes: /docs/getting-started/, /docs/cli/, /docs/faq/, /concepts/what-is-geo/, /compare/e-geo-vs-geo-optimizer-skill/, /compare/geo-tools-2026/.
- The string "terminal" must NOT appear in landing copy.

## Verify + finish

- Extend site/verify.sh: keep all existing checks + assert: JSON-LD SoftwareApplication + Organization on /, entity sentence, answer block, hero answer-card element, sitemap includes /, no 'terminal' in dist/index.html. `npm run build` && `bash verify.sh` must pass — show the output.
- Conventional commits. End with: branch, commit hashes, verify output summary, Lighthouse-style weight report (bytes of / assets).
