# Reveal.js deck

This directory now contains a local Reveal.js presentation built from the talk outline in `lean-presentation-plan.md`.

## Run

From this directory:

```bash
python3 -m http.server 8000
```

Then open `http://127.0.0.1:8000`.

## Files

- `index.html`: the slide deck
- `styles.css`: the custom theme
- `assets/`: self-contained logo/font assets used by the deck
- `vendor/reveal/`: vendored Reveal.js 5.2.1 runtime assets
- `lean-presentation-plan.md`: the source outline the deck follows

## Notes

- The deck uses Reveal's nested sections, so each major part of the talk is a vertical stack.
- `hash: true` is enabled, so slide URLs update as you navigate.
- The notes plugin is loaded, so speaker view is available with the usual Reveal shortcuts.
- The deck is self-contained for GitHub Pages deployment and no longer depends on assets outside `presentation/`.
