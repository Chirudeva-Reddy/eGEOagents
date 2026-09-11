# TASK: Correct the composition back to a deliberate midpoint — not tiny, not oversized

Work in the existing E-GEO repo at cwd on the current branch. The previous composition pass was stopped because it over-corrected: it reduced the headline to `3.7vw`, made the citation visual too small, removed the viewport-height feel, and produced a page that looked like half of a normal hero. Fix the actual files now.

## Preserve

- The Swiss/brutalist system: white canvas, black ink, 2px grid, Archivo/grotesk, chartreuse #D4FF00 only as a graphic accent.
- The current persistent citation-field SVG + requestAnimationFrame motion implementation from commit 3961a78. Do not replace, simplify, or make the animation decorative/tiny.
- Current copy, CTA labels, SEO/GEO structured data, canonical entity sentence, answer block, sections, links, and no-terminal rule.
- No dark/orange SlashStack styling, no terminal, no code-block aesthetic.

## The required midpoint

The target is a confident, normal full hero section — approximately 80–92% of a 1440×900 viewport after the compact header. It must feel intentional and spacious, not a tiny dashboard and not a four-line billboard that consumes everything.

At 1440×900:

1. **Hero height:** set the hero composition to fill roughly the first viewport (`min-height: clamp(720px, calc(100svh - 72px), 860px)` or a visually equivalent result). The next section should begin at/just below the fold, not halfway up the screen.
2. **Two-column balance:** left content roughly 7/12, animated citation field roughly 5/12. Both columns should have substantial visual weight. The citation graphic must occupy approximately 40–55% of the hero height and be readable without zooming — not a small strip.
3. **Headline:** larger than the failed tiny version, smaller than the original full-width billboard. Use a strong display scale around 5.5–7vw at desktop with a max size around 7–8rem, constrained to the left column and intentionally wrapped into roughly 3 lines. It should dominate the left side while leaving the citation field visible beside it.
4. **Copy and stats:** enough explanatory copy to make the product clear, with normal editorial spacing. Do not compress everything into a tiny stack.
5. **CTA:** compact max-content group under the copy. The primary button should be visible and confident; secondary/research links support it. No CTA link may stretch across the full 12-column row. No giant horizontal CTA band.
6. **Citation field:** bring the existing animated graph into the first viewport at a meaningful scale. It can extend to the lower edge of the hero, but it must not be an afterthought below it. Preserve the moving lines, tokens, answer node, and citation signal.

At 390×844:

- Stack the hero cleanly; the headline must be readable and not consume the entire viewport.
- Keep the CTA group compact (buttons may stack only as content-width controls, not full-page bands).
- Citation field follows with a meaningful mobile height (not a thumbnail) and no horizontal overflow.
- The first page should feel like one complete hero, not a miniature desktop squeezed into mobile.

## Implementation guidance

- Undo the tiny values introduced by the previous pass, but do not restore the original full-width CTA row.
- Use CSS grid and `min-height`/`clamp` values; do not solve with arbitrary fixed pixel offsets that break at 768/390.
- The hero visual must be visible in the first viewport; do not rely on a below-fold IntersectionObserver to reveal it.
- Content visible by default; motion enhances only.
- Keep animation running in normal mode, paused on `visibilitychange`, and composed/static under reduced motion.

## Verification required before commit

Run build and verify. Use Playwright at 1440×900 and 390×844 and report concrete measurements:
- hero bounding height and citation-field bounding height;
- CTA group bounding width versus viewport width (prove it is not full-width);
- no horizontal overflow on mobile;
- motion state changes over 5 seconds.
Capture screenshots if available, but do not rely only on code inspection.

Do not merge or deploy. Commit only after build, verify, and browser checks pass. Report commit, measured dimensions, and verification output.
