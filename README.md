# Lyndhurst Pizza — Online Ordering Website

Single-page website for Lyndhurst Pizzeria (446 Ridge Rd, Lyndhurst, NJ) with a digital menu, online ordering (no online payments — cash or card by phone), anti-prank order confirmation, and an owner admin panel for editing the menu.

## Files

| File | What it is |
|---|---|
| `index.html` | The entire website (HTML + CSS + JS in one file) |
| `menu.json` | The published menu. The site loads this automatically. Owner updates it via the admin panel. |

## How ordering works

1. Customer builds an order from the menu, picks **Pickup or Delivery** and **Cash or Card by phone**.
2. Order is emailed to the shop (if `ORDER_ENDPOINT` is configured) and/or sent by the customer via a one-tap pre-filled **text message** from their own phone.
3. The text from the customer's real number **is the confirmation** — kitchen rule: never start an order until it's confirmed by text or a call to the customer.
4. Anti-spam: valid phone required, confirmation checkbox, 10-minute per-browser cooldown, every ticket marked `UNCONFIRMED` until verified.

## Setup before going live (edit the config block at the top of the `<script>` in `index.html`)

- `ADMIN_PASSWORD` — **change it.** (Note: it's client-side only; it gates the editing UI, not real security. Publishing still requires access to this repo/hosting.)
- `ORDER_ENDPOINT` — create a free form at https://formspree.io with the shop's email and paste the endpoint URL so orders arrive by email.
- `SHOP_SMS_NUMBER` — the number that receives order texts.
- Verify all menu prices — the initial menu was transcribed from an **old printed menu** and needs to be checked against current register prices (use the owner panel).

## Owner: editing the menu

1. Open the site, click **Owner login** in the footer, enter the password.
2. Add / edit / delete items and categories. Changes preview instantly on your browser.
3. Click **"Download menu.json to publish"** and replace `menu.json` in this repo with the downloaded file.
4. Commit — the live site updates for everyone.

## Free hosting with GitHub Pages

1. In this repo: **Settings → Pages**.
2. Under "Build and deployment", set Source to **Deploy from a branch**, pick `main` and `/ (root)`, save.
3. Your site goes live at `https://<username>.github.io/<repo-name>/` within a minute or two.
4. Optional: connect the custom domain (lyndhurstpizza.com) in the same Pages settings screen.

## Disclaimer

Prices online may differ from in-store; the shop confirms the total with every order. No payment data is ever collected by this site.
