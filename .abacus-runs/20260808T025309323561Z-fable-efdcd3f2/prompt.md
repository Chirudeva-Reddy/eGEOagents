# TASK: Rebuild the egeoagents.com landing from zero — cinematic, editorial, ZERO terminal aesthetic

BUILD NOW in the repo at cwd (auto-branch from main). No web search. No questions.

CONTEXT: two previous attempts were rejected by the owner. Rejection reasons, in his words: (1) too plain/default-looking; (2) the terminal/CLI framing — E-GEO's buyer is NOT a terminal person. This product lives in the world of the web and AI search: founders, marketers, site owners, SEO people whose customers now ask ChatGPT/Perplexity instead of Googling. **ABSOLUTELY NO terminal windows, NO shell prompts, NO code blocks as hero or decorative elements.** Installation commands may appear ONLY as small copy-chips in the install section (facts, not aesthetics).

The quality bar is a cinematic, editorial, motion-rich site: film grain, native GLSL shader layer, GSAP word-by-word reveals, magnetic CTAs, one accent color on warm black, generous whitespace, serif display type. Reference vibe: an A24-graded editorial page about the shift from search engines to answer engines.

## Product facts (verified, use only these)

- E-GEO — open-source Generative Engine Optimization (GEO) & Answer Engine Optimization (AEO) toolkit (Python CLI + Claude Code skills), based on published GEO research (arXiv:2511.20867). MIT. 147 stars, 42 forks (as of 2026-08).
- What it does: analyzes any web content, scores it against 10 research-backed GEO features, rewrites it into citable form, and generates the JSON-LD schema answer engines reward. Plus a reproducible evaluation harness and a continuous monitoring loop.
- Install: `pip install egeo` or `npx skills add https://github.com/mverab/eGEOagents` (install section only).
- Links: https://github.com/mverab/eGEOagents · https://arxiv.org/abs/2511.20867 · internal routes /docs/getting-started/, /docs/cli/, /docs/faq/, /concepts/what-is-geo/, /compare/e-geo-vs-geo-optimizer-skill/, /compare/geo-tools-2026/.

## Creative spec

**Aesthetic:** warm black #0B0B0B, bone white #F5F1EA, ONE accent (amber #E8A857 preferred). Film grain overlay ~8%. Serif display headline (Fraunces or equivalent), Inter body, JetBrains Mono only for micro-labels. Forbidden: terminal windows, neon, cyan glow, circuit boards, gradient blobs, corporate centered SaaS layout, emoji, stock-feeling illustrations.

**Hero (100vh, left-aligned editorial, 8vw padding):**
1. Mono micro-label, amber, fades in first: `◆ open-source geo · aeo toolkit`
2. Headline, GSAP word-by-word (blur 20→0, y 40→0, 0.08s stagger). Write it for the BUYER's pain — the shift from search to answers. Direction (improve freely): "your customers stopped searching. they started asking." with one word accent-shifted to amber.
3. Subtitle, one honest sentence: E-GEO makes your content the answer — analyze, rewrite, and schema-mark your pages so ChatGPT, Perplexity, Gemini, and Claude cite you.
4. **Hero visual (the centerpiece — NOT a terminal):** an elegant, animated "answer engine" moment in pure DOM/CSS/JS: a real question (e.g. "what's the best way to optimize content for AI search?") resolving into an AI-answer card that cites a source — with the citation slot being the emotional point (your site belongs there). Abstracted, cinematic UI card, not a screenshot of any real product, no logos of OpenAI/Perplexity (use neutral engine glyphs/labels like "answer engine"). Subtle float/parallax. Alternative if you have a stronger concept: a constellation/web of questions flowing into cited answers. Whatever you build: it must feel like the web, not a dev tool.
5. CTAs: primary `get started →` (/docs/getting-started/), ghost `★ star on github`, text-link `read the research ↗`. Magnetic hover on primary.
6. Bottom strip, mono, 40% opacity: `147★ · 42 forks · mit · arxiv:2511.20867`.

**Shader layer:** one subtle GLSL background effect (ink-bleed / fluid SDF / fine drifting grain), throttled rAF, pause on tab blur, prefers-reduced-motion → static, WebGL-missing → static gradient fallback.

**Sections after hero:** the shift (2-3 editorial sentences + one strong stat-free statement: answer engines are the new front page) → how it works (3 steps as editorial cards: analyze → rewrite → get cited — NO code, use plain words + small diagrams/icons) → capabilities (4-6 cards: 10-feature scoring, content rewriting, JSON-LD schema generation, reproducible evaluation, continuous monitoring loop, Claude Code integration) → honest dated comparison table (data from site/src/content/docs/compare/geo-tools-2026.md, "Last verified: 2026-08-05") → install (two copy-chips, minimal) → final CTA → footer.

**Hard SEO/GEO requirements (non-negotiable):**
- SoftwareApplication JSON-LD on / (MIT, codeRepository, citation arXiv:2511.20867, offers price 0, author Person Miguel Vera sameAs github.com/mverab) + global Organization JSON-LD preserved.
- Canonical entity sentence verbatim, visible HTML: "E-GEO — open-source Generative Engine Optimization (GEO) & Answer Engine Optimization (AEO) toolkit (Python CLI + Claude Code skills), based on published GEO research (arXiv:2511.20867)."
- Answer block 50-170 words as crawlable HTML text.
- All internal links to the real existing routes listed above.

## Technical

- Serve `/` from a custom Astro page (src/pages/index.astro); REMOVE the Starlight splash (site/src/content/docs/index.mdx) so routes don't collide; Starlight keeps /docs/*, /concepts/*, /compare/* untouched; fix sidebar if it referenced the splash.
- Vanilla Astro + GSAP (npm) allowed; no React/Next. Static output. Landing total < 400KB. Fonts subset.
- Responsive 375/768/1440. Lighthouse 90+ desktop. Semantic landmarks, AA contrast.
- Extend site/verify.sh: keep all existing checks + assert JSON-LD, entity sentence, answer block, answer-card hero element, sitemap includes /. `npm run build` + `bash verify.sh` must pass — show output.
- Explicitly verify: the string "terminal" does not appear in the landing copy, and no shell/prompt UI elements exist.

## Finish

Conventional commits. End with: branch name, commit hashes, verify output, accent color, one-paragraph rationale for the hero concept you chose.
