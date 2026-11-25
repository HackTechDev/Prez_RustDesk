# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

An unmodified copy of **reveal.js 6.0.2** (HTML presentation framework), checked in as the base for a RustDesk presentation (`prez/rustdesk`). The presentation itself lives in `index.html` (in French), built from the tutorial in `../../tutoriel/` (`item.md`, `SECURITY.md`, and the Marp outline, demo script and Q&A in `presentation/`). Its own styling is `assets/rustdesk.css` (overrides the `black` theme's CSS variables, adds `.card`/`.callout`/`.cols` helpers and classes for the inline SVG diagrams); screenshots are in `assets/rustdesk/`. Speaker notes (`<aside class="notes">`) carry the demo timings. Most work here is authoring slides, not changing the framework.

To preview with all fragments visible, append `?fragments=false` to the URL (reveal.js reads config overrides from the query string).

`index.html` loads the **prebuilt files in `dist/`** (`dist/reveal.js`, `dist/theme/*.css`, `dist/plugin/*.js`) via plain `<script>`/`<link>` tags and calls the global `Reveal.initialize({...})`. `dist/` is committed, so the deck works without a build step; only rebuild if you change sources under `js/`, `css/` or `plugin/`.

## Commands

Requires Node >= 22.12 (enforced via `devEngines`). `node_modules` is not installed by default: run `npm install` first.

- `./runServer.sh` — serves the repo statically with PHP at http://127.0.0.1:40779 (no Node needed; uses committed `dist/`).
- `npm start` — Vite dev server on port 8000 (override with `npm start --port=XXXX`).
- `npm run build` — full build: `tsc`, core lib, styles/themes, each plugin, then banner. Outputs to `dist/`.
- `npm run build:styles` — rebuild only `css/reveal.scss`, `css/reset.css` and every `css/theme/*.scss` into `dist/`. New theme files in `css/theme/` are picked up automatically.
- `npm test` — runs every `test/*.html` QUnit page in headless Chrome (Puppeteer) against a Vite server on port 8009. There is no single-test flag; to run one, open `http://localhost:8000/test/<file>.html` under `npm start`, or temporarily narrow the glob in `scripts/test.js`.
- `npm run package` — zip the presentation (`scripts/zip.js`).
- React wrapper (`react/`, separate package): `npm run react:build`, `npm run react:test`, `npm run react:demo`. See `react/AGENTS.md` for its lifecycle/sync invariants.

There is no CI: the upstream reveal.js GitHub workflows were removed. Run `npm run build && npm test` locally if you change the framework sources.

## Architecture (framework, if you need to touch it)

- `js/index.ts` — library entry; wraps `js/reveal.js` (the `Deck` factory) and adds the legacy single-instance global `Reveal.initialize()` API with queued calls.
- `js/reveal.js` — core deck: holds state and wires up one instance of each controller in `js/controllers/` (keyboard, fragments, backgrounds, auto-animate, overview, scroll view, print view, notes, plugins, etc.). Controllers receive the deck instance and are the place to look for feature-specific behavior.
- `js/config.ts` — `RevealConfig` type and defaults; `js/reveal.d.ts` — public API types.
- `plugin/<name>/` — each built-in plugin (highlight, markdown, math, notes, search, zoom) has `plugin.js`, an `index.ts` entry and its own `vite.config.ts`; built separately into `dist/plugin/`.
- `css/reveal.scss` + `css/layout.scss` — core styles; `css/print/` — PDF/paper print styles.
- Themes: each `css/theme/<name>.scss` includes `template/mixins.scss`, `template/settings.scss` (CSS variables to override), then `template/theme.scss`. To make a custom theme, copy an existing one, override settings, then `npm run build:styles` and link `dist/theme/<name>.css` from `index.html`.
- Vite aliases (`vite.config.ts`) map `reveal.js` → `/js` and `reveal.js/plugin` → `/plugin` so sources can be imported as if from the published package.
- `examples/` and `demo.html` show most features (markdown, math, auto-animate, backgrounds, layout helpers) and are good references when writing slides.

## Formatting

Prettier (`.prettierrc`): tabs, single quotes, print width 100, ES5 trailing commas.
