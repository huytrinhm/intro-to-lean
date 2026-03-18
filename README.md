# Lean Slides Repo

This repository contains a Reveal.js presentation about Lean, plus the two Lean books it draws from as git submodules:

- `fp-lean`
- `theorem_proving_in_lean4`

The presentation lives in `presentation/`.

## Clone

```bash
git clone --recurse-submodules <your-repo-url>
```

If you already cloned without submodules:

```bash
git submodule update --init --recursive
```

## Local preview

```bash
cd presentation
python3 -m http.server 8000
```

Then open `http://127.0.0.1:8000`.

## GitHub Pages

The workflow in `.github/workflows/pages.yml` deploys the contents of `presentation/` to GitHub Pages on pushes to `main`.

After pushing this repository to GitHub:

1. Create the GitHub repository and add it as `origin`.
2. Push `main` with `git push -u origin main`.
3. In the repository's Pages settings, make sure the publishing source is `GitHub Actions` if GitHub has not already selected it automatically.

For a project repository, the site URL will typically be:

```text
https://<your-user-or-org>.github.io/<repo-name>/
```
