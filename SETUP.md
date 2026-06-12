# Brush & Soul Studio — build & launch guide

The site design and content are done (see `index.html`, `commissions.html`, `about.html`). This guide covers the account-side steps to turn it into a live Shopify store with Printify syncing to both the website **and** Etsy.

## The architecture, in one line

**Printify is the hub.** Caroline edits a product once in Printify, and it publishes to *both* Etsy and the new Shopify site automatically. Orders from either store route back to Printify for fulfillment on their own. No more double data entry.

```
                 ┌──→ Etsy (existing)
   PRINTIFY ─────┤
   (master)      └──→ Shopify site (new)
```

---

## Phase 1 — Stand up Shopify (≈30 min)

1. Create a free **Shopify Partner** account → partners.shopify.com.
2. From the Partner dashboard, create a **development store** (free, no time limit while building).
3. In the store admin, install the **Printify** app from the Shopify App Store.
4. Pick a plan later — Basic (~$29–39/mo) is fine to launch. The dev store stays free until you're ready to go live.

## Phase 2 — Get the theme into the store (≈30 min)

The files in this folder are the *design*. Two ways to turn them into the live Shopify theme — I'll do the actual port; you just connect the pipes:

1. Create a **GitHub repo** for the theme (same as your other sites).
2. In Shopify: **Online Store → Themes → Add theme → Connect from GitHub**, and point it at that repo. This is the official Git integration — every push version-controls and updates the theme.
3. Locally, install the **Shopify CLI** (`npm i -g @shopify/cli`) and run `shopify theme dev` for live local preview while I build out the Liquid sections from the design.

> Base it on Shopify's free **Dawn** theme — I'll layer the Brush & Soul design (the arch motif, palette, type, the funnel and commission sections) on top of it as custom sections.

## Phase 3 — The catalog (≈1–2 hrs)

1. In Printify, **Manage my stores → Add store → Shopify**, connect the dev store.
2. Confirm her existing **prints** are real Printify products. Any that were only ever built by hand in Wix need to be (re)created in Printify so they sync.
3. **Publish** the prints to Shopify — Printify pushes listings with mockups, variants, and pricing. They now auto-sync on Shopify *and* Etsy.
4. Build the **Products** line (phone cases, mugs, apparel, etc.) in Printify and publish — same automatic sync.
5. Add the **original paintings** (the $600–$1,200 one-of-a-kind pieces) manually in Shopify admin, inventory = 1 each. These are not POD.
6. Leave **Etsy connected** the whole time — nothing about it changes.

## Phase 4 — Commissions, events, content

- The **commission intake form** (`commissions.html`) currently shows a thank-you on submit. To make it deliver, wire it to email/Shopify on the live site — simplest is a Shopify contact-form app or a Formspree/email endpoint. I'll set this up during the port.
- The **estimator** uses your base prices ($300 / $600 / $900 / $1,200). The material/detail upcharges in it are clearly-labeled placeholders — set the real percentages when you have them and I'll lock them in.
- **Events** is a simple page Caroline updates in the Shopify admin — no code needed.

## Phase 5 — Domain & go-live

1. Point **brushandsoulstudio.com** at Shopify (transfer the domain, or just update DNS — Shopify gives exact records).
2. Build a **redirect map** from the old Wix URLs (`/product-page/...`, `/category/...`) to the new Shopify URLs so search rankings and existing links survive. Shopify has a built-in URL Redirects tool.
3. Test one real order end-to-end through Printify.
4. **Decommission Wix** once the new site is verified live.

---

## What I still need from you

1. **Brand assets** — the logo, background art/graphics to reuse, any brand font, and a batch of product images. These replace the marked placeholders.
2. **The dev store + GitHub repo connected** (Phases 1–2) so I can push the Liquid theme.
3. **Material/detail upcharges** for the estimator — or confirm base-only for now.
4. **Commission medium pricing** — flat by size, or does acrylic vs watercolor change the base.

Send those and the static design becomes a working store.
