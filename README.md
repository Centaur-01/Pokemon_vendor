# Pokémon Vendor Storefront

A static, QR-code **price-lookup storefront** for a trading-card vendor. Every
physical card and sealed product carries a QR sticker; scanning it opens that
item's live page — current price, image, and details. **The sticker never
changes; the page does.**

**Live:** https://centaur-01.github.io/Pokemon_vendor/

## What it does
- **Scan → price.** Each item has a permanent Item ID (CC-####) encoded in its QR.
- **Browse & search** the vendor's for-sale inventory: search by name, filter by
  region (🇺🇸/🇯🇵) and era, tap a card for the full view.
- **Fast & free to host.** Pure static site (HTML + JSON) on GitHub Pages — no
  server, loads on spotty show-floor signal.
- **Self-hosted images.** Card pictures live in `card-img/` so they can't break
  if an upstream source goes down.

## How it works
This repo hosts the **public storefront only**. The page reads `inventory.json`
(the for-sale listings) directly in the browser:

```
index.html          the storefront (search, tabs, card modal, QR hash-routing #<id>)
inventory.json      public listings (price, image, item id) — generated, not hand-edited
catalog.csv         id-sorted listing feed (used by the vendor's price sheet)
card-img/           self-hosted card/product images
review.html         image-QA "swipe to confirm" tool for the vendor
```

Prices come from the vendor's own pricing (their market data + their overrides).
Reference images are stock photos for identification, not the exact card.

## What's *not* in this repo
The pricing engine, source inventory data, and operational tooling live in a
separate **private** repository — this public repo only carries what the
storefront needs to render. Intent, progress, and the running worklog are
tracked privately there.

---
*Static storefront generated from a Collectr export. Not affiliated with,
sponsored by, or endorsed by Nintendo / The Pokémon Company.*
