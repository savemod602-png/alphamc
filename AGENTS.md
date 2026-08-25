# AGENTS.md

## Architecture

This project is a single static HTML file (`index.html`) with no backend, no build tooling, and no database. Everything — markup, CSS, and JavaScript — lives inline in that one file for easy deployment as a static site.

State (categories, products, tier rosters, cart, monthly goal %, recent purchases, admin login flag) is persisted entirely client-side via `localStorage`, keyed under `alphamc_*` names near the top of the `<script>` block. On first load, defaults seed `localStorage`; afterward, stored values take precedence.

## Key directories

- `index.html` — the entire site (styles, markup, and logic).
- `alpha.toml` — publishes the repo root as-is (no build command needed).

## Conventions

- Admin credentials are hardcoded in the script (`ADMIN_EMAIL` / `ADMIN_PASSWORD`) — this is a static site with no server-side auth, so treat this only as a UI gate, not real security.
- All "Buy Now" / checkout actions link to the Discord invite (`DISCORD_URL` constant) rather than a real payment flow.
- Player skins in the tiers section are fetched from `https://minotar.net/avatar/<name>/32.png` using the Minecraft username as entered by the admin.
- Fade-up scroll animations use an `IntersectionObserver` (`observeFadeUps()`), called after any re-render that introduces new `.fade-up` elements.
- Any change to categories/products/tiers/goal/purchases/cart must be followed by a corresponding `saveLS(...)` call to persist it, then a re-render of the affected section.

## Non-obvious decisions

- No framework or bundler was used since the request explicitly called for a single portable HTML file.
- No Netlify Database or Blobs usage: all data is intentionally ephemeral per-browser (per the request, "no external database is required").
.
