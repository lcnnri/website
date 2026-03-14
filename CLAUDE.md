# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Live preview with auto-reload (port 7274)
quarto preview

# Build the site to docs/
quarto render
```

The output directory is `docs/`, which is used for deployment (e.g., GitHub Pages).

## Architecture

This is **Luca Neri's personal academic website** — a Quarto-based static site for a researcher/economist. Treat content (paper titles, abstracts, author names, affiliations, links) as authoritative: do not rewrite or embellish it. When adding new papers or sections, follow the existing formatting patterns exactly.

**Source files** (`.qmd`) are Quarto markdown with YAML frontmatter — edit these for content changes. They compile to HTML in `docs/`.

**Key files:**
- `_quarto.yml` — project config: theme (`lumen`), navbar, footer, CDN includes (Bootstrap Icons, Academicons), preview port
- `styles.css` — all custom styling; also copied to `docs/styles.css` on render
- `index.qmd` — home/landing page
- `research.qmd` — publications and working papers (most complex page)

**Research page interactivity** (`research.qmd`): Paper entries use inline JavaScript for collapsible abstracts and BibTeX sections with copy-to-clipboard. Each paper has pill-style link buttons (Journal, arXiv, PDF, Code, Abstract, BibTeX). The toggle logic lives directly in `<script>` blocks within the `.qmd` file.

**Styling conventions in `styles.css`:**
- CSS custom properties for the color palette (defined on `:root`)
- Paper cards use `.paper-card` with left-accent borders
- Responsive breakpoint at 768px
- Grid layout via Bootstrap's `.g-col-*` classes from Quarto

## UX Design Principles

**Content is the product.** The research is what visitors come for. UI elements exist to surface content, not to decorate it. Resist adding visual complexity that competes with the work itself.

**Credibility through restraint.** Academic audiences distrust fussy or overly "marketed" designs. Prefer clean typography, generous whitespace, and a muted color palette. Avoid animations or layouts that feel promotional.

**Scannable research listings.** Papers should be skimmable at a glance — title, venue/year, and co-authors visible without any interaction. Abstracts and BibTeX are secondary; keep them collapsible.

**Friction-free access to outputs.** Every paper should have a direct link to the most accessible version (PDF, arXiv, SSRN). Do not bury downloads behind hover states or multiple clicks.

**Typography first.** Body text should be readable at a comfortable size and line length (~65–75 characters). Hierarchy comes from weight and spacing, not decorative elements.

**No dead ends.** Every page should give the visitor a clear next action: download CV, read a paper, send an email. If a page doesn't serve a clear purpose for a visitor, it shouldn't exist.

**Fast and functional on all devices.** Academics visit from conference laptops, phones, and old university computers. Layouts must degrade gracefully; interactive elements must work reliably.

**Consistent, predictable interactions.** Buttons and links should behave the same way everywhere. A pattern established on one page (e.g. pill-style paper links) should be used uniformly across the site.
