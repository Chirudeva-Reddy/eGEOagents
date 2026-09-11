# TASK: Replace the answer-engine name rail with real SVG brand marks

Work in the existing E-GEO repo at cwd, current branch, from commit `1645235`. This is a narrow visual polish change. Do not redesign anything else.

## Requested change

The current answer-engine rail is a small horizontal marquee containing plain text names:
ChatGPT, Perplexity, Gemini, Claude.

Replace the plain text items with recognizable, production-quality SVG brand marks/icons for the four answer engines. Keep the rail compact and editorial, consistent with the Swiss/brutalist landing. Do not make it a large logo wall or add a new section.

Use verified brand SVG paths from a reputable open icon source/package (for example the Simple Icons package, if its current entries exist), or carefully vendor the exact SVG paths into the site. Do not invent approximations, draw fake logos, or hotlink fragile third-party images at runtime. Keep the source local and deterministic.

Required marks:
- OpenAI/ChatGPT mark (use the brand mark, with accessible label “ChatGPT”)
- Perplexity mark, with accessible label “Perplexity”
- Google Gemini mark, with accessible label “Gemini”
- Anthropic Claude mark, with accessible label “Claude”

## Accuracy and trademark semantics

The rail must not imply official integrations, partnerships, or compatibility guarantees. Preserve or improve the label to something like:
`Answer engines / the surfaces where sources get named`

Each SVG mark needs an accessible text fallback (`aria-label`, visually-hidden label, or equivalent). Visible text names may be omitted if the marks are clear, but accessibility must remain.

## Visual and motion constraints

- Preserve the current rail position, size, marquee speed, clipping, hover/focus pause, reduced-motion behavior, and no-overflow behavior.
- Marks should be monochrome black/grey by default, with the existing chartreuse accent used only on hover/focus if tasteful. Do not introduce brand colors that break the Swiss system.
- Keep marks large enough to recognize but not oversized; this is a credibility detail, not a hero.
- Preserve the entire hero and citation-field SVG/rAF animation byte-for-byte where practical; do not redesign or re-layout the hero.
- No terminal, code, dark/orange styling, rounded SaaS cards, or generic logo grid.

## Verification contract

Modify `site/verify.sh` so the declared artifact changes. Preserve all prior checks and add checks that:
- the four engine marks/accessible labels are present;
- no old plain-text-only rail implementation remains;
- the honest non-partnership label remains;
- citation-field motion marker and `requestAnimationFrame` remain;
- no horizontal overflow at 1440×900 and 390×844.

Run `npm run build`, `bash verify.sh`, and a browser check confirming each mark renders, the marquee transforms, hover/focus pause still works if practical, and the main citation animation still changes over 5 seconds.

Commit this narrow change. Do not merge or deploy. Report the commit, source used for the SVG marks, and verification output.
