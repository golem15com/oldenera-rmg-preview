# Repository Guidelines

## Project Structure & Module Organization

This repository is a dependency-free static browser app for reviewing Olden Era `.rmg.json` map templates.

- `index.html` is the GitHub Pages entry point.
- `template-reviewer.html` is the local working copy of the reviewer page.
- `README.md` documents user-facing usage and deployment notes.
- `.github/workflows/pages.yml` deploys the root to GitHub Pages on pushes to `master`.
- `.nojekyll` disables Jekyll processing for Pages.

There is no build output directory, package manifest, or asset tree. CSS and JavaScript are embedded in the HTML files, so keep related UI, style, and behavior changes close together.

## Build, Test, and Development Commands

- `python3 -m http.server 8000` starts a local static server. Open `http://localhost:8000/`.
- Opening `index.html` directly in a browser works for quick checks.
- `git status --short` verifies the working tree.

There is no install, build, lint, or automated test command. Do not introduce tooling unless the change clearly needs it.

## Coding Style & Naming Conventions

Use the existing plain HTML/CSS/JavaScript style:

- Two-space indentation for HTML, CSS, and JavaScript blocks.
- Semantic HTML where practical; use lowercase kebab-case classes such as `.graph-panel`.
- CSS custom properties belong in `:root`; reuse existing color and spacing variables before adding new ones.
- Prefer small, focused JavaScript functions with descriptive camelCase names.

Work locally in `template-reviewer.html`. Update `index.html` only when the changes are ready to release to GitHub Pages.

## Testing Guidelines

Testing is manual. During development, load `template-reviewer.html` in a browser and verify:

- The page renders without console errors.
- `Load .rmg.json` accepts a local template file.
- Summary metrics, graph rendering, filters, and detail panels still work.
- Layout remains usable at desktop and narrow viewport widths.

Use representative `.rmg.json` files locally. Do not commit private template data.

## Commit & Pull Request Guidelines

Git history uses short imperative or descriptive messages, for example `Set up GitHub Pages deployment`. Keep commits focused and avoid mixing unrelated formatting with behavior changes.

Pull requests should include a summary, manual test notes, and screenshots for visible UI changes. Link related issues when available and mention any GitHub Pages impact.

## Security & Configuration Tips

The app runs fully in the browser and should not upload selected template files. Preserve that privacy property when adding features. Avoid external scripts, tracking, or remote asset dependencies unless explicitly required and reviewed.
