# Silverplay Collection Page — Project Context

**Repo:** kanchantechinfinity/silverplaycollectionpage
**Live:** https://kanchantechinfinity.github.io/silverplaycollectionpage/
**Scope:** a single static HTML landing page (Ganpati Collection) for
silverplay.in — no framework, no build step, deployed via GitHub Pages
directly from `main`.

## Files
- `index.html` — the live page (GitHub Pages entry point).
- `preview.html` — byte-for-byte mirror of `index.html`, kept in sync
  manually for local preview. Any edit to one must be applied to both.

## Design system (inherited from the live site, do not change)
Dark ink/void background, `--sepia` (gold, `#B8860B`-family) accents,
ivory/parch text tones, serif display font for headings. Governing
instruction from the original styling request: subtle ancient-Indian
heritage motifs only — never change existing colors, fonts, buttons, or
section structure/spacing.

## Heritage ornamentation layer
Added purely-additive decorative CSS + a few inline `<svg><use></svg>`
elements: jaali lattice veils, mandala watermarks, paisley corner vines,
temple arcade/vine edge bands, a 9-slice manuscript border, lotus
flourishes under headings, a medallion rule between sections. Every
ornament is `aria-hidden="true"` and `pointer-events:none`; backgrounds
use `isolation:isolate` on the section (`.orn-sec`) so `z-index:-1`
layers paint above the section's own background instead of behind it —
same pattern as `silverplayproject`'s `.heritage-sec`, see
[[silverplay-scroll-carousel]] there for the sticky-positioning gotcha
this same pattern can cause if a section ever needs a sticky descendant
(not applicable here — this page has no sticky/scroll-driven sections).
SVG `<symbol>` defs for the reused marks (`#orn-lotus`, `#orn-medallion`,
`#orn-sprig`) live in a hidden sprite sheet near the top of the file.

## Gotchas
- Several product images (and the original hero) are
  `lh3.googleusercontent.com/aida/...` or `/aida-public/...` URLs — AI
  design-tool-generated mockup imagery, not real product photography.
  `/aida/` (no "-public") is a private, session-scoped link that can
  403 once the session expires; `/aida-public/` is durable. If any
  image on this page goes invisible again, check its URL path first —
  swap a broken `/aida/` link for a working `/aida-public/` one already
  used elsewhere on the page rather than sourcing a new external image.
- At least one product photo (Ganesh Charan Paduka coin) has a fake
  browser-chrome mockup baked into its own pixels (an artifact of
  whatever AI tool generated it) — pre-existing, not a bug to "fix"
  unless the user asks about that specific image.
- No build/typecheck step exists for this project — verification is
  visual (open in the Browser pane) only.
