# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Classroom is a static, front-end-only HTML/CSS prototype for a virtual classroom platform (French UI). There is no build step, package manager, framework, or backend — it's plain HTML files linked to a single stylesheet. Content is static/hardcoded demo data (no data fetching, no state persistence).

## Running the project

There is nothing to build or install. Open the HTML files directly in a browser, or serve the directory with any static file server, e.g.:

```
python -m http.server 8000
```

Then visit `http://localhost:8000/index.html`.

## Architecture

```
classe-virtuelle/
├──📄 index.html
├──📄dashboard.html
├──📄classe.html
├──📁css/
│   └──📄style.css
├──📄.gitignore
├──📄CLAUDE.md
└──📄README.md
```

Three pages, navigated via plain `window.location.href` redirects in inline `onclick` handlers (no router, no JS framework):

- `index.html` — login screen (`body.page-login`). The "Se connecter" button navigates straight to `dashboard.html`; there is no real authentication.
- `dashboard.html` — admin dashboard (`body.page-dashboard`): sidebar nav, stat cards, weekly planning grid, live online-students list, and a classes/sessions table. "Rejoindre"/"Lancer" buttons navigate to `classe.html`.
- `classe.html` — live virtual classroom view (`body.page-classe`): video/participant tiles, chat sidebar, and a control bar. "Terminer" navigates back to `dashboard.html`. Contains one inline `<script>` that runs a `setInterval` to increment the session timer display (`.timer`) — the only JS in the project.

All three pages share a single stylesheet, `css/style.css`, organized into clearly delimited sections per page (search for the banner comments `PAGE LOGIN`, `PAGE DASHBOARD`, `PAGE CLASSE VIRTUELLE`). Shared/reset rules (box-sizing, scrollbar styling, `.pulse` animation, `.spacer`) live at the top of the file before the page sections. When adding styles for a given page, add them to that page's section rather than creating a new file.

Styling conventions already in use:
- Font is Google Font `Matangi`, imported via `@import` at the top of `style.css`.
- Colors are hardcoded hex values repeated inline (e.g. `#3498db` blue, `#2ecc71` green, `#f39c12` orange, `#8e5fd8` purple, `#2c3e50` dark navy) — there are no CSS custom properties/variables defined, so match existing hex values rather than inventing new ones for the same semantic color (blue = math/primary, green = success/online, orange = pending/warning, purple = accent, red = live/recording/mic-off).
- Many icons are inline hand-authored SVGs directly in the HTML rather than an icon font/library — follow the same pattern (viewBox="0 0 24 24", stroke-based) when adding new icons.
- `.dist` is an empty placeholder directory; there is no actual build output.

## Notes for this environment

- Working directory: `C:\Users\giuse\OneDrive\Desktop\classe-virtuelle`. This directory is a subfolder inside a much larger git repository rooted at the user's home directory (`C:\Users\giuse`); most of that outer repo is unrelated personal/config data. Do not assume standard project-root git conventions apply beyond this folder.
