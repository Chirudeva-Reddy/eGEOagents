# TASK: Rebalance the E-GEO landing composition — preserve the approved citation animation

Work in the existing repo at cwd, current branch. Continue from the latest successful motion implementation (commit 3961a78 / Fable session 123f9458c8). The owner approved the new animated citation field and said "adelante" to this composition iteration.

## What is approved and MUST NOT be broken

- Swiss/brutalist visual system: white field, black ink, hard 2px grid, Archivo/grotesk, restrained chartreuse #D4FF00 graphic accent.
- Current inline SVG citation-field animation: persistent requestAnimationFrame loop, moving citation signal, flowing lines, answer/source nodes, pause/resume on visibilitychange, reduced-motion fallback. Preserve the SVG structure and motion code; do not replace it with a static card or a new generic animation.
- Current copy, CTAs wording, SEO/GEO JSON-LD, canonical entity sentence, answer block, internal links, comparison table, install chips, and footer.
- No terminal/shell/code visual language. No dark SlashStack styling.

## Owner's composition feedback to fix

The current first viewport is structurally sound but awkward:
- The headline is so huge and full-width that it consumes almost the whole first screen.
- The CTA row is enormous and stretches left-to-right across the entire grid, overpowering the page.
- The citation field animation is pushed below the first fold instead of being part of the initial visual story.
- It feels unconventional in a way that is not yet intentional enough.

## New composition target

Recompose the hero as a deliberate two-part Swiss editorial layout that communicates the product in one viewport:

### Desktop 1440
- Keep header compact.
- Use a 12-column grid with headline/copy/CTAs on the left (roughly columns 1–7) and the animated citation field on the right (roughly columns 8–12), or an equally strong asymmetric variation.
- Headline remains bold and Swiss, but reduce its maximum scale and line count enough that it no longer occupies nearly the whole screen. It should feel dominant, not suffocating. Aim for 2–3 lines in the left column, not 4 huge full-width lines.
- Put the subcopy and stats below/alongside the headline without creating a massive separate horizontal band.
- Make CTAs compact, inline or grouped within the left content column. The primary CTA may be black with chartreuse hover, but it must NOT be a full-width 5/12 block or a giant row spanning the page. Secondary and research links should read as supporting actions.
- Bring the `citation-field` into the hero composition so its continuous motion is visible before the first major scroll. It can extend vertically into the next section, but its core graph must be visible in the first viewport.
- First hero viewport should feel complete at 1440x900: headline, explanation, compact CTAs, and a meaningful portion of the animated citation field all visible.

### Tablet/mobile 768/390
- Preserve the hierarchy: headline first, compact CTA group second, citation field immediately after/alongside — not an enormous CTA band.
- Ensure no horizontal overflow and keep the graph legible. The first viewport may scroll on mobile, but avoid oversized headline consuming all usable height.
- Keep animation running and observable on mobile where performance allows; reduced-motion must still render a composed static graph.

## Implementation constraints

- Prefer CSS grid changes and small markup relocation over rewriting the hero. Reuse existing classes where possible.
- Do not solve this by shrinking everything into a tiny page. Preserve visual confidence and whitespace.
- Do not remove the hard grid rules; use them to make the new asymmetry intentional.
- CTA links should have clear hit targets but no full-width decorative blocks.
- Content must remain visible by default; no new opacity-zero gating.

## Verification

Modify `site/verify.sh` only if needed, preserving all current checks. Add/keep checks for:
- `citation-field` and motion loop still present.
- No terminal string.
- JSON-LD/entity/answer/sitemap checks pass.
- Build passes.
- Use Playwright screenshots or DOM measurements at 1440x900 and 390x844 to confirm:
  - hero contains the citation field in the first viewport at desktop;
  - CTA group does not span the full 12-column width;
  - no horizontal overflow at mobile;
  - motion state still changes over 5 seconds.

Do not merge or deploy. Commit the composition correction and report commit hash plus verification evidence.
