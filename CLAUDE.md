# Project notes for Claude

Renters in Recovery: a one-page tenant-rights and advocacy site for Illinois sober living residents. Static HTML + Sass, bundled with Parcel, deployed to GitHub Pages. Built on the Newbie FEM Starter Pack.

## Content rules

- Anything said about a named organization or person must be attributed to a filing ("the complaint alleges..."). Never state an allegation as fact.
- `src/docs/` holds the published filings. Redact third parties' names, addresses and phone numbers before adding a document, and flatten the PDF so the text layer can't be copied out. Never publish the court exhibits (they include an ID card).

## Scripts

- `npm start`: Parcel dev server on port 4321. Writes to `dist-dev/`, never `dist/`.
- `npm run build`: clean production build in `dist/` with relative paths (`--public-url ./`).
- `npm run push-gh`: builds, then publishes `dist/` to the `gh-pages` branch. Requires the `origin` remote to use SSH.
- `npm run format`: Prettier over `src/`.

## Sass

- 7-1 pattern with `@use`/`@forward`, never `@import`. `abstracts/` outputs no CSS; partials pull it in with `@use "../abstracts" as *;`.
- `breakpoints()` mixin: `sm` 16rem, `md` 48rem, `lg` 62rem, `xl` 75rem. Mobile-first.
- `$palette` becomes `--color-*` in `themes/_default.scss`, mapped to semantic `--theme-*` tokens. Components use only `--theme-*`.
- BEM: one partial per block in `components/`.
