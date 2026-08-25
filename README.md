# ALPHA MC

A single-file, static website for the "ALPHA MC" Minecraft server: a store, BoxPvP tier rankings, and an admin panel for managing everything.

## Tech

- Plain HTML, CSS, and vanilla JavaScript — no build step, no framework.
- Canvas API for the animated falling-snow background.
- `localStorage` for all persistence (categories, products, tiers, cart, monthly goal, recent purchases, admin login state).
- [minotar.net](https://minotar.net) API for rendering player skins in the tiers section.

## Running locally

Just open `index.html` in a browser, or serve the directory with any static file server, e.g.:

```bash
npx serve .
```

## Admin access

Click "Admin" in the navbar and log in with the hardcoded owner credentials embedded in `index.html`. Once logged in, a "Panel" button appears for managing categories, products, tier rosters, the monthly goal, and recent purchases. All changes save to `localStorage` immediately.
