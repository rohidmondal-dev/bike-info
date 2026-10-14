# AGENTS.md

Project: informative motorbike website built with latest HTML/CSS standards and best practices. GitHub portfolio piece — keep code and content portfolio-quality.

Static site. No build, no dependencies, no tests, no CI.

## Run

Serve repo root with Node.js or Bun only (no Python): `npx serve .` or `bunx serve .`, then open `index.html`. If the port is taken, `serve -l` silently falls back to a random port — read the `Accepting connections at` line, and kill stale servers via the PID owning the port.

## Verify

Use `playwright-cli` for UI checks and verification (run `playwright-cli --help` for full command list). Always open headed and go fullscreen with the F11 key, e.g. `playwright-cli open --headed <url>`, then `playwright-cli press F11` (never `resize` for fullscreen; use `open --mobile` for narrow-viewport checks). F11 does not always take effect — confirm with `eval` on `window.innerWidth` before trusting a screenshot. Use `screenshot` / `snapshot` to see and confirm work.

## Structure

- Pages at root: `index.html`, `types.html`, `safety.html`, `contact.html`. No templating — header/nav/footer markup is duplicated per page.
- Styles: `css/main.css` only imports layers (`reset > tokens > base > layout > components`). Put shared variables in `css/tokens.css`, never hardcode colors/spacing. `css/home.css` is the homepage-only Night pass theme, scoped under `body.theme-night` — other pages stay on the light base theme.
- `index.html` additionally links `css/home.css` plus Google Fonts (Anton display, Inter body); other pages are system-font only.
- `assets/icons/`, `assets/images/` are empty (`.gitkeep` only). Add files there and reference with relative paths.
- `favicon.svg` at root, linked per page.

## Conventions

- When adding/editing a page, copy the existing boilerplate: doctype, `meta viewport/description/theme-color`, `favicon.svg` + `css/main.css` links, skip-link, `site-header` nav, `site-footer`.
- Update `aria-current="page"` on the nav link matching the current page.
- Homepage hero has a single-run load animation (beam sweep, staggered rise, tach fill) guarded by `prefers-reduced-motion`. Keep it to one orchestrated sequence — no loops or scattered effects.
- Contact form in `contact.html` is a static placeholder (`action="#"`, `method="get"`). Do not expect submissions to work without wiring a backend/service first.
- Only `index.html` has real motorbike copy. Other pages are still placeholder text — keep their semantic structure (`main#main`, `h1`, `.lead`) when replacing it.
