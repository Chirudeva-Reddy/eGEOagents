# TASK: Fix the E-GEO landing's missing cinematic motion — motion-first implementation, not another static redesign

Work in the existing repo at cwd, on the current branch. This is a correction to the Swiss/brutalist landing that is already built. Do NOT redesign the copy, information architecture, SEO, or general Swiss visual system. Do NOT create a new throwaway mockup. Implement real, visible, persistent animation in the actual `site/src/pages/index.astro`.

## Verified failure diagnosis (must address)

The current page only has:
- a one-time CSS word reveal (opacity/blur/translate, ~1 second), and
- one-shot IntersectionObserver clip-path reveals on scroll.

There is no persistent animation, no GSAP, no canvas/WebGL, no animated SVG system, and no @keyframes loop. At rest it is a static white Swiss page. The owner rated it 3/10: structure is acceptable, cinematic idea is absent. Do not claim a reveal is a cinematic experience.

## Creative goal

Keep the approved Swiss/brutalist direction: white field, black ink, hard 2px grid, Archivo/grotesk, restrained chartreuse #D4FF00 only as graphic accent. The cinematic object must be an editorial visualization of the WEB moving into the ANSWER ECONOMY — not a terminal, not code, not a generic SaaS dashboard, not a SlashStack dark/orange layout.

Build a living "citation field" in the hero: a bold, large-scale SVG/canvas information graphic occupying the right half / lower hero. It should show questions entering, resolving into an answer, and citation/source nodes connecting to it. E-GEO's marked source node is the visual payoff. It must feel like information design / motion poster, not a floating rounded UI card.

Required continuous behavior in normal mode (observable after at least 5 seconds at rest):
- thin black connection lines draw/pulse continuously between question nodes, answer node, and source nodes;
- 2–4 small question/source nodes travel along paths or appear/disappear with staggered timing;
- the answer/citation node has a restrained pulse or scan state;
- one chartreuse mark/line moves through the graph as the "citation" signal;
- motion is deterministic, slow, elegant, and grid-snapped — no flashy neon, no particle soup, no bouncing cards.

Use one of these production-safe approaches, preferably inline SVG + GSAP (add gsap dependency if needed), or a well-designed requestAnimationFrame canvas with an accessible DOM fallback. Native SVG/GSAP is preferred because lines/nodes remain crisp and inspectable. The graphic must not be the only meaning: preserve a crawlable HTML explanation of the answer-card/citation concept.

## Motion quality requirements

- Use GSAP or a real requestAnimationFrame/SVG animation loop for persistent ambient motion; CSS-only one-shot reveal is insufficient.
- The first viewport must visibly change between 0s and 5s without user interaction or scroll.
- No animation may be gated behind IntersectionObserver. IntersectionObserver can enhance below-fold sections only, never hide required hero content.
- `prefers-reduced-motion: reduce`: render a composed final frame with all nodes/lines visible, no loop, no opacity-zero content.
- Pause expensive animation on `visibilitychange` and resume without resetting the composition.
- No layout shift: reserve hero visual dimensions from first paint.
- Keep all text crawlable and visible by default.
- Do not use terminal/shell/code-block visual language anywhere in the landing. The string `terminal` must remain absent from dist/index.html.
- Do not use a video or stock image in this correction; the motion graphic must be code-native.

## Preserve exactly

- Current copy/CTAs unless a tiny adjustment is necessary for the visual.
- Current SEO/GEO JSON-LD, canonical entity sentence, answer block, internal links, compare table, install chips, and footer.
- Swiss palette and typography. Do not introduce dark+warm SlashStack styling.

## Verification contract

Modify `site/verify.sh` and add checks that prove the failure is fixed:
- `index.html` contains the hero motion root (e.g. `citation-field`), SVG/canvas, and an explicit animation implementation marker (`gsap`, `requestAnimationFrame`, or `data-motion-loop`).
- `index.html` contains `prefers-reduced-motion` fallback and visibility handling.
- `index.html` contains a persistent animation declaration/loop, not just reveal transitions.
- Existing JSON-LD/entity/answer/sitemap/no-terminal checks continue to pass.
- Run `npm run build && bash verify.sh`.
- Use Playwright or another available browser script to load `/`, wait 5 seconds, and record that the animation state changes / active animations exist. If screenshots are practical, capture hero at 0.5s and 5s and compare hashes or pixel difference; do not just report that the code exists.

## Finish

Commit the correction on the current branch. Report: commit hash, exact build/verify output, animation mechanism chosen, and the concrete browser verification proving the hero changes over 5 seconds. Do not deploy or merge.
