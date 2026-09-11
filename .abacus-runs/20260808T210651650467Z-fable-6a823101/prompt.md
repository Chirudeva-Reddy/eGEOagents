# TASK: Add restrained scroll motion and a small answer-engine credibility rail

Work in the existing E-GEO repo at cwd, current branch, from the approved composition commit `ca31043`. This is a small polish pass for v1. Do NOT redesign the hero or alter its layout, scale, copy, CTA placement, or approved citation-field SVG/rAF animation.

## Owner's request

The current landing is acceptable but not yet 7/10. Add only enough polish to make the page feel alive as the visitor descends:

1. Very subtle scroll-reveal motion for below-fold sections.
2. Optionally, a restrained editorial rail/carousel of answer-engine names to add legitimacy. It is not required if it makes the page noisier; if added, it must be small and tasteful.

## Required scroll polish

- Add a reusable `.scroll-reveal` enhancement to selected sections/cards as they enter the viewport: roughly 10–18px translate + slight opacity/filter/clip transition, 500–800ms, stagger only where it improves hierarchy.
- Content must be visible by default. Never leave entire sections at `opacity: 0` waiting for IntersectionObserver. Use a progressive enhancement class added by JS, with a timeout/fallback that reveals anything stuck.
- Do not affect the first hero layout or the persistent citation-field animation.
- Respect `prefers-reduced-motion: reduce`: no movement, all content immediately visible.
- Pause/avoid unnecessary work when the document is hidden.
- Ensure the animation is apparent during a normal scroll pass but subtle enough not to look like a template demo.

## Answer-engine rail (small, optional but preferred)

Add a compact typographic/editorial rail near the transition after the hero or before the answer explanation — not a new giant section and not a set of generic rounded logo cards.

Use names only, ideally as a slow horizontal marquee or restrained alternating rail:
`ChatGPT · Perplexity · Gemini · Claude`

Label it accurately, for example: `ANSWER ENGINES / THE SURFACES WHERE SOURCES GET NAMED` or equivalent. Do NOT call these official integrations, partners, supported platforms, or compatibility guarantees. E-GEO is an open-source toolkit that helps content become more understandable and citable to answer engines; preserve factual honesty.

If using wordmarks, use accessible text and CSS/typography — do not download trademark images or invent logos. The rail should pause on hover/focus and become static under reduced motion. It must not cause horizontal page overflow; use an intentional clipped marquee container.

## Preserve exactly

- Swiss/brutalist white/black 2px grid, Archivo/grotesk, chartreuse `#D4FF00` accents.
- Hero headline, compact CTAs, current hero height and two-column balance.
- `#citation-field` SVG, its `requestAnimationFrame` motion, visibility pause/resume, and reduced-motion fallback.
- Current SEO/GEO JSON-LD, answer block, entity sentence, links, comparison, install and footer content.
- No terminal, shell, code-block, dark/orange SlashStack, or generic SaaS-card aesthetic.

## Verification contract

Modify `site/verify.sh` so the declared artifact is actually modified and add checks for whichever elements are implemented (e.g. `scroll-reveal`, reduced-motion fallback, `engine-rail` if added), while preserving all existing checks. Run:
- `npm run build`
- `bash verify.sh`
- browser check at 1440×900 and 390×844 for no horizontal overflow;
- scroll from top to bottom and confirm all content is visible after the pass;
- confirm citation-field motion still changes over 5 seconds;
- confirm reduced-motion path does not hide content if possible.

Capture screenshots only if useful. Commit the small polish pass. Do not merge or deploy. Report the commit, build/verify output, and whether the engine rail was included or intentionally omitted.
