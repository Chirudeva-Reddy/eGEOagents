# TASK: 3 radically divergent design directions for the egeoagents.com landing — hero-only mockups

BUILD NOW. No web search. No questions. Create a branch (e.g. chore/design-variants) and put three self-contained static HTML files at repo-root `design-variants/` (NOT inside site/ — these are throwaway, Astro must not build them): `a-editorial-light.html`, `b-blueprint.html`, `c-swiss.html`. Each must render standalone (inline CSS/JS, system fonts or Google Fonts CDN link allowed).

## The failure you must avoid

Two previous attempts were rejected for looking generic and identical to another of the owner's products (SlashStack), whose visual signature is: near-black background (#0A0A0C), off-white text (#EDEDE8), single warm orange/amber accent, mono micro-labels, centered UI cards. **FORBIDDEN in all three variants:** dark background + light text + single warm accent as the core scheme; mono-font micro-labels; the "glowing UI card on dark bg" trope; terminal/shell anything; neon/cyan; gradient blobs.

## Product + approved copy (reuse this copy; it passed review)

- Product: E-GEO — open-source GEO/AEO toolkit that makes web content get cited by ChatGPT, Perplexity, Gemini, Claude. Buyer: founders, marketers, site owners, SEO people — NOT terminal devs.
- Headline direction: "your customers stopped searching. they started asking."
- Sub: E-GEO analyzes, rewrites, and schema-marks your pages so answer engines cite you.
- CTAs: primary `get started →`, ghost `★ star on github`, text `read the research ↗`.
- Stats: `147★ · 42 forks · mit · arxiv:2511.20867`.
- Hero visual concept (reinterpret freely per direction): a real question resolving into an AI-answer card whose citation slot is the emotional point — the web, not dev tools.

## The three directions (each must feel like a different studio made it)

**A — editorial light:** paper/cream background (#FAF7F2 or similar), black ink typography, magazine layout with thin rules and generous columns, ONE non-warm accent (e.g. deep blue or forest green). Serif display headline. Think: a print annual report about the web. Motion notes: subtle fade/line-draw reveals.

**B — blueprint / cartography of answers:** the web as a technical map — fine grid lines, node-and-edge diagram where questions flow into cited sources, annotation labels, blueprint palette (either classic blue-on-white blueprint or ink-navy with pale lines — your choice, but NOT the forbidden dark+warm scheme). The answer-card becomes a node in the map. Precise, systematic, beautiful like an information-design poster.

**C — swiss / brutalist:** stark white (or pure black with WHITE as the only "accent"), enormous grotesk headline (tight tracking, Helvetica/Neue Haas class), hard visible grid, almost no ornament, one fluorescent accent max (e.g. #D4FF00 or pure red — pick per scheme). Confidence through typography alone.

Each file: hero at 1440×900 viewport fill + enough below-the-fold hint (first section start) to judge the system. Real HTML text (crawlable pattern), responsive-ish (must not break at 390 width). At the bottom of each file add an HTML comment: palette hexes, fonts, and 3 bullets on the intended motion language.

## Finish

Commit the three files. End with: branch name, commit hash, and a 2-line summary per variant of what makes it visually distinct from the other two and from the forbidden SlashStack scheme.
