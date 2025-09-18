<!-- .github/copilot-instructions.md - guidance for AI coding agents -->
# Assistant guidance for the StevenBook workspace

This repository is a very small static-site project containing a couple of HTML pages and an `images/` folder. The goal of edits should be minimal, safe, and directly tied to page content, layout, or small static-assets fixes.

Key files to reference
- `AboutMe.html` — primary page. Uses an inline CSS card and a background image at `./images/Richie Rich Mansion.jpg`.
- `hello.html` — simple standalone page with large "Hello Word" text.
- `ReadMe..txt` and `temporary note.txt` — informal notes; no build tasks.
- `images/` — contains local assets referenced by the HTML files.

Big-picture architecture and intent
- This is a static, single-directory website (no build system, no package manager, no server-side code). Changes are typically direct edits to the HTML/CSS or replacing/adding images.
- Keep changes small and reversible: prefer editing the HTML/CSS and image files over introducing new tooling.

Project-specific patterns and conventions
- Files use relative paths to images (e.g. `./images/Richie Rich Mansion.jpg`) — preserve relative linking and be cautious about spaces in filenames when suggesting automated renames.
- CSS is embedded in the `<style>` block within each HTML file. Prefer local edits (update the style block) rather than extracting to new files unless requested.
- There is no JavaScript or templating system. If adding interactivity, keep it minimal and self-contained in the HTML file.

Developer workflows
- No build, test, or package commands are present. Typical workflows are:
  - Edit HTML/CSS in place.
  - Preview by opening the file in a browser (file://) or a simple static server (e.g., `python -m http.server` in the project folder) if cross-origin restrictions occur for background images.
  - When adding/changing images, update `src`/CSS `url()` references to the relative path and avoid spaces where possible.

Examples of safe edits
- Fix text typos (e.g. change "Hello Word" to "Hello World" in `hello.html`).
- Improve accessibility by adding `alt` text to images and `lang` attributes (files already have `lang="en"`).
- Normalize image filenames (replace spaces with dashes) but update all references and note that renaming is a breaking change for anyone using file:// paths; prefer creating a copy with a new name and updating references.

What not to do
- Do not introduce heavy build tooling (Webpack, Node) or large frameworks without explicit user approval.
- Do not remove or rewrite the project into a different website architecture.

Searchable anchors and files to check when making changes
- `AboutMe.html` — background image usage, contact link to `hello.html`, inline CSS variables.
- `hello.html` — simple display text that is likely intended to be corrected or styled.

If you need more context
- Ask the user whether they want to: convert this into a small static site generator structure, host it, or keep it as simple HTML files.

After making edits
- Run a quick smoke check by opening the edited HTML in a browser or running a simple static server and confirm the background image and links work.

Request for feedback
- I created these instructions from the current files. Tell me which areas are unclear or if you want the guidance expanded (deployment steps, hosting, CI, or moving to a generator).
