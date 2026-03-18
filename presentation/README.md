# Reveal.js deck

This directory now contains a local Reveal.js presentation built from the talk outline in `lean-presentation-plan.md`.

The authoring source is split across `src/template.html` and `src/slides/*.html`. The top-level `index.html` in this directory is generated output for static hosting.

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
- `src/slides/`: slide fragments grouped by presentation section
- `build-slides.mjs`: regenerates `index.html` from the split source files
- `index.html`: generated slide deck for static hosting
- `styles.css`: the custom theme
- `assets/`: self-contained logo/font assets used by the deck
- `vendor/reveal/`: vendored Reveal.js 5.2.1 runtime assets
- `lean-presentation-plan.md`: the source outline the deck follows

## Notes

- The deck uses Reveal's nested sections, so each major part of the talk is a vertical stack.
- `hash: true` is enabled, so slide URLs update as you navigate.
- The notes plugin is loaded, so speaker view is available with the usual Reveal shortcuts.
- The deck is self-contained for GitHub Pages deployment and no longer depends on assets outside `presentation/`.
- GitHub Pages rebuilds the deck from `src/` during deployment, so the split source remains the canonical edit path.
