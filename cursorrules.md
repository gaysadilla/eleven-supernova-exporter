# Project Context
You are building a custom **Supernova.io Documentation Exporter**.
This project transforms Design System data into a static documentation website.

# Tech Stack
- **Templating:** Handlebars / Pulsar (.pr files in `src/`).
- **Styling:** SCSS (in `scss/`).
- **Logic:** TypeScript (in `typescript/`).
- **Build:** Webpack.

# Official Documentation (Reference These!)
- **Exporter Development:** https://developers.supernova.io
  (Use this for Pulsar syntax, SDK references, and `exporter.json` config).
- **General Platform:** https://learn.supernova.io
  (Use this to understand what "Blocks", "Tokens", or "Blueprints" are).

# Critical Workflow: Styling
The browser ONLY reads `assets/dist/docs.min.css`. It does NOT read SCSS files directly.
WHENEVER you modify a file in `scss/`:
1.  **Edit** the SCSS file (prefer `scss/custom-overrides.scss` for safety).
2.  **Run** `npm run build` in the terminal.
3.  **Verify** that `assets/dist/docs.min.css` has changed.
4.  **Commit** both the source SCSS and the compiled CSS.
5.  **Push** to GitHub: `git push origin master` (or your branch name).

# "Global Token" Strategy
We do NOT hardcode colors in module files (like `top-navigation.scss`).
1.  Define brand tokens in `scss/custom-overrides.scss` (e.g., `--brand-primary`).
2.  Map Supernova's system variables to those brand tokens in the same file.
    Example:
    ```scss
    :root { --brand-purple: #8223d2; }
    .style-light { --topNavBackground: var(--brand-purple); }
    ```

# Git Workflow
ALWAYS commit and push changes after making modifications:
1.  **Stage** changes: `git add <files>` (include both source files and compiled outputs).
2.  **Commit** with a descriptive message: `git commit -m "Description of changes"`.
3.  **Push** to remote: `git push origin master` (or your branch name).
4.  **Verify** changes appear on GitHub.

# Project Goals
1.  **Rebranding:** Fully customize the look to match "Eleven" branding.
2.  **Custom Blocks:** Create new documentation blocks for specific needs later.