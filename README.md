# Nursing Budget Planner — Landing Page

A single-page marketing site for the **Nursing School Budget Planner**, a downloadable budgeting + scholarship-tracking tool sold on Payhip. The page links to the Payhip product for checkout; the paid planner file itself is delivered through Payhip after purchase (see the note below).

**Buy link:** https://payhip.com/b/kHBuE

## What's in this repo

| File | Purpose |
| --- | --- |
| `index.html` | The landing page. Self-contained (all CSS inline) so it works on GitHub Pages with zero build steps. |
| `demo.html` | A public, try-before-you-buy demo of the planner. Budgeting works fully; Excel export, save/load, and the full scholarship list are disabled and prompt to buy. Safe to publish. |
| `favicon.svg` | Browser tab icon (periwinkle heart). |
| `.nojekyll` | Tells GitHub Pages to serve the files directly, skipping Jekyll processing. |
| `README.md` | This file. |
| `LICENSE` | Copyright / usage terms. |

## Deploy it free with GitHub Pages

1. Create a new repository on GitHub (public).
2. Upload every file in this folder to the repo root (including the hidden `.nojekyll`).
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose the `main` branch and the `/ (root)` folder, then **Save**.
5. Wait about a minute. Your site goes live at `https://<your-username>.github.io/<repo-name>/`.

### Optional: use your own domain
Add a file named `CNAME` (no extension) containing just your domain, e.g. `nursebudget.com`, then point your domain's DNS at GitHub Pages per GitHub's docs.

## Editing the page

Everything you'll likely want to change lives in `index.html`:

- **Price** — the page shows `$19.99`. Search for `$19.99` (it appears in the nav button, hero, pricing card, and final call-to-action) and replace each with your price. Also update the pricing card's big number: look for `<span class="cur">$</span>19<span class="cents">.99</span>`.
- **Payhip link** — the buy URL `https://payhip.com/b/kHBuE` appears on every button. Search-and-replace it if your product link ever changes.
- **Brand name** — "Nursing Budget Planner" appears in the nav, footer, and `<title>`. Rename to your store/product name if you prefer.
- **Colors** — the palette is defined once at the top of the `<style>` block as CSS variables (`--peri-700`, `--heart`, etc.), matching the planner itself.
- **Copyright / disclaimer** — bottom of the file, in the footer.

### Want Payhip's on-site checkout overlay instead of a link?
The buttons currently open your Payhip product page in a new tab (simple and reliable). If you'd rather have the checkout pop up over the landing page, add Payhip's script before `</body>`:

```html
<script src="https://payhip.com/payhip.js"></script>
```

and give each buy button `class="payhip-buy-button"` with `data-product="kHBuE"`. See Payhip's own embed instructions for the current attributes.

## Important: keep the paid file out of this public repo

This repo is your **free storefront**. Do **not** upload the full `nursing-budget-planner.html` product file here — a public site would let anyone download the thing you're selling for free. Keep the full planner as the **Payhip download** only.

`demo.html` is the safe, public version to host: it's fully interactive for budgeting, but Excel export, save/load, and the complete scholarship list are turned off and prompt visitors to buy. Publish `demo.html`; keep the full planner on Payhip.

## License

See `LICENSE`. The landing-page code here is your own to deploy for your product; it isn't intended for redistribution as a template.
