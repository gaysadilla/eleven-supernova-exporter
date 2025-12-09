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
**⚠️ CRITICAL: The browser ONLY reads `assets/dist/docs.min.css`. It does NOT read SCSS files directly.**

**MANDATORY STEPS - DO NOT SKIP ANY:**
WHENEVER you modify a file in `scss/`:
1.  **Edit** the SCSS file (prefer `scss/custom-overrides.scss` for safety).
2.  **MUST BUILD:** Run `npm run build` in the terminal. This compiles SCSS → CSS.
3.  **MUST VERIFY:** Check that `assets/dist/docs.min.css` actually changed (search for your new CSS rule).
4.  **MUST COMMIT:** Stage and commit BOTH files together:
    ```bash
    git add scss/custom-overrides.scss assets/dist/docs.min.css
    git commit -m "Description of changes"
    ```
5.  **MUST PUSH:** Push to GitHub: `git push origin master` (or your branch name).
6.  **Wait 2-3 minutes** for Supernova to sync from GitHub before publishing.

**If you skip step 2 (build), your changes will NOT appear in Supernova!**

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
1.  **Stage** changes: `git add <files>` (include both source files AND compiled outputs like `assets/dist/docs.min.css`).
2.  **Commit** with a descriptive message: `git commit -m "Description of changes"`.
3.  **Push** to remote: `git push origin master` (or your branch name).
4.  **Verify** changes appear on GitHub (check the commit on GitHub.com).

**For SCSS changes specifically:** Always commit both the `.scss` source file AND the compiled `assets/dist/docs.min.css` file together.

# Project Goals
1.  **Rebranding:** Fully customize the look to match "Eleven" branding.
2.  **Custom Blocks:** Create new documentation blocks for specific needs later.