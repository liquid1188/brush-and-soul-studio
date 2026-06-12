# Brush & Soul Studio — Go-Live Runbook

Everything buildable is done and in three repos:

- **Theme:** `liquid1188/brush-and-soul-theme` (connect to Shopify)
- **Originals import:** `originals-shopify-import.csv` (4 originals, ready to upload)
- **Newsletter endpoint:** `liquid1188/brush-and-soul-subscribe` (deploy to Vercel)

Already pre-wired into the theme so you don't have to touch them: nav, all page
content, Instagram (@likoudesigns) + Etsy (Likoudesigns), the newsletter endpoint
URL, and the homepage featured section (points at the Originals collection).

Do the phases in order. Est. ~40 min total. Steps only you can do (they need logins).

---

## Inputs needed from you before starting
- [ ] **Studio email** (for the Contact page + order notifications)
- [ ] Does Caroline already have a **Printify** account, or start fresh?
- [ ] Keep the Vercel project named `brush-and-soul-subscribe` (so the pre-wired
      endpoint URL matches). If you rename it, tell me and I'll update one line.

---

## Phase 1 — Store + theme (~10 min)
1. Create the Shopify store at shopify.com (start the free trial; **Basic** plan is
   enough to launch). Set store name **Brush & Soul Studio**, currency, address.
2. **Online Store → Themes → Add theme → Connect from GitHub** → authorize →
   pick `liquid1188/brush-and-soul-theme`, branch `main`.
3. Click **Preview**. If it looks right, **Publish**. (If anything errors, send me
   the message — same-day fix.)

## Phase 2 — Products (~10 min)
4. **Products → Import** → upload `originals-shopify-import.csv` → Import.
   The 4 originals appear (qty 1, manual fulfillment — Caroline ships them).
5. Install **Printify** (Shopify App Store) → in Printify, connect this store.
   Build/sync her **prints + merch** → **Publish to Shopify**. (Printify also keeps
   her Etsy in sync — same catalog, both storefronts.) **Tag** each Printify product
   `Prints` or `Products` so the collections below catch it automatically.

## Phase 3 — Collections + pages (~10 min)
6. **Products → Collections → Create** (Smart collections):
   - **Originals** — condition: *Product tag is equal to* `Originals`
   - **Prints** — *Product tag is equal to* `Prints`
   - **Products** — *Product tag is equal to* `Products`
7. **Online Store → Pages → Add page** ×4. Title each and set its **theme template**
   (Body can stay empty — content lives in the theme):
   - About → template `page.about`
   - Commissions → template `page.commissions`
   - Events → template `page.events`
   - Contact → template `page.contact`
8. **Theme editor →** open the **Contact** page → set the **Studio email**.
   (Featured collection, socials, newsletter are already set.)

## Phase 4 — Filters + newsletter (~10 min)
9. Install the free **Search & Discovery** app → enable filters on collection pages
   (Availability, Price, Product type). That powers the shop filtering.
10. **Newsletter → Resend:**
    - Create a **new Resend account** for the studio (separate from any other).
    - **Audiences → create** ("Brush & Soul Studio") → copy the **Audience ID**.
    - **API Keys → create** → copy the key.
    - Deploy `liquid1188/brush-and-soul-subscribe` to **Vercel** (Import from GitHub,
      keep the name).
    - Vercel → **Settings → Environment Variables**: add
      `RESEND_API_KEY` and `RESEND_AUDIENCE_ID` → **Redeploy**.
    - Test: submit the homepage form → the contact should appear in the Resend audience.

## Phase 5 — Domain + cutover (~10 min, do last)
11. **Settings → Domains → Connect existing domain** `brushandsoulstudio.com`.
    Update DNS at the registrar per Shopify's instructions.
12. **Online Store → Navigation → URL Redirects** — add redirects from old Wix paths
    to the new ones for anything indexed (product pages, /shop, etc.).
13. Once the domain verifies and orders test clean, **decommission Wix**.

---

## After go-live (fast-follows, optional)
- Welcome email on signup (needs her domain verified in Resend first) — I can add it.
- Lock the subscribe endpoint's CORS to her domain (currently open `*`).
- Real event dates (replace the example listings in the theme's Events section).
- Confirm commission estimator upcharge numbers with Caroline (placeholders now).
