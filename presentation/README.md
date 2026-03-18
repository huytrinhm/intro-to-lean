# Reveal.js deck

This directory now contains a local Reveal.js presentation built from the talk outline in `lean-presentation-plan.md`.

The authoring source is split across `src/template.html` and `src/slides/*.md`. The top-level `index.html` in this directory is generated output for static hosting.

## Run

Rebuild the deck after editing slide source files:

```bash
node build-slides.mjs
```

Then, from this directory:

```bash
python3 -m http.server 8000
```

Then open `http://127.0.0.1:8000`.

## Files

- `src/template.html`: the outer deck shell
- `src/slides/`: Markdown slide fragments grouped by presentation section
- `build-slides.mjs`: regenerates `index.html` from the split source files
- `index.html`: generated slide deck for static hosting
- `styles.css`: the custom theme
- `assets/`: self-contained logo/font assets used by the deck
- `vendor/reveal/`: vendored Reveal.js 5.2.1 runtime assets
- `lean-presentation-plan.md`: the source outline the deck follows

## Authoring

- Use `.md` slide files. The build step wraps them in Reveal's built-in `data-markdown` sections.
- Markdown files may mix multiple slides in one file:
  - `---` starts a new horizontal slide.
  - `--` starts a new vertical slide within the current stack.
- Use Reveal's Markdown comment syntax for attributes:
  - `<!-- .slide: class="r-vstack justify-center section-slide" -->`
  - `Text here <!-- .element: class="fragment" -->`
- Markdown slides get `content-slide` by default during the build unless they already declare their own `<!-- .slide: ... -->` attributes.
- Raw HTML is still allowed inside Markdown when a slide needs more control.

## Notes

- The deck uses Reveal's nested sections, so each major part of the talk is a vertical stack.
- `hash: true` is enabled, so slide URLs update as you navigate.
- The deck is self-contained for GitHub Pages deployment and no longer depends on assets outside `presentation/`.
- GitHub Pages rebuilds the deck from `src/` during deployment, so the split source remains the canonical edit path.
