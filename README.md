# Khata

*your money, tracked*

Khata is a single-file, offline-first personal finance ledger. It's a budgeting app, savings-pot tracker, portfolio overview, and IOU list rolled into one page — no build step, no backend, no dependencies beyond two Google Fonts.

## Features

- **Home** — total wealth at a glance: savings pots, existing portfolio, and net IOU position, plus a suggested "move" for the current month based on your surplus.
- **Budget** — monthly take-home, rent, and recurring costs/investments, with the ability to skip a recurring item for one month or add one-off costs and extra income. Tracks a spending cap as a percentage of take-home.
- **Pots** — configurable savings pots (Emergency fund, ETF/ISA, Pension, Indian equity) with opening balances, monthly additions, and an auto-suggested contribution plan based on that month's surplus.
- **Portfolio** — existing holdings in GBP and INR, converted to a single GBP total using a live GBP→INR exchange rate (fetched from public FX APIs, editable manually).
- **Owed** — track money owed to you and money you owe, factored into a "true net position."
- **Backup/restore** — export the full state as a JSON file (or share it, on supported devices) and re-import it later.

## Running it

No build tools or server required — just open the file:

```
index.html
```

directly in a browser, or serve the folder with any static file server, e.g.:

```
npx serve .
```

It also works as an installable PWA (manifest + icon are embedded inline in the HTML).

## Data & storage

All data lives in the browser: it's saved to `localStorage` on the device (and to Claude's `window.storage`, if that host is present) under the key `khata_v2`. Nothing is sent to a server except:

- an FX rate lookup (`frankfurter.app` / `open-er-api.com`) to convert INR holdings to GBP.

If a browser context can't persist data (e.g. some in-app webviews), the app shows a banner warning that changes won't be saved, and recommends opening it in a normal browser tab.

Use **Export backup** / **Import backup** on the Home tab before clearing browser data or switching devices.

## Tech

Plain HTML/CSS/JS, no framework, no build pipeline — everything lives in [index.html](index.html).
