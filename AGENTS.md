# AGENTS.md

Project: informative motorbike website built with latest HTML/CSS standards and best practices. GitHub portfolio piece — keep code and content portfolio-quality.

Static site. No build, no dependencies, no tests, no CI.

## Run

Serve repo root with Node.js or Bun only (no Python): `npx serve .` or `bunx serve .`, then open `index.html`.

## Verify

Use `playwright-cli` for UI checks and verification (run `playwright-cli --help` for full command list). Always open headed and maximize via resize, e.g. `playwright-cli open --headed <url>`, then `playwright-cli resize 1920 1080`. Use `screenshot` / `snapshot` to see and confirm work.

## Structure

- Pages at root: `index.html`, `types.html`, `safety.html`, `contact.html`. No templating — header/nav/footer markup is duplicated per page.
- Styles: `css/main.css` only imports layers (`reset > tokens > base > layout > components`). Put variables in `css/tokens.css`, never hardcode colors/spacing elsewhere.
- `assets/icons/`, `assets/images/` are empty (`.gitkeep` only). Add files there and reference with relative paths.
- `favicon.svg` at root, linked per page.

## Conventions

- When adding/editing a page, copy the existing boilerplate: doctype, `meta viewport/description/theme-color`, `favicon.svg` + `css/main.css` links, skip-link, `site-header` nav, `site-footer`.
- Update `aria-current="page"` on the nav link matching the current page.
- Contact form in `contact.html` is a static placeholder (`action="#"`, `method="get"`). Do not expect submissions to work without wiring a backend/service first.
- All page copy is placeholder text. Keep semantic structure (`main#main`, `h1`, `.lead`) when replacing it.
