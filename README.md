# Nursing School Budget Planner

A calm, step-by-step budget planner for nursing students, plus a landing page
that sells it as a **one-time $12.99** purchase. Pure static site — HTML, CSS
and a little JavaScript. No build step, no backend.

## What's in here

| File            | What it is                                                        |
| --------------- | ----------------------------------------------------------------- |
| `index.html`    | Landing page (hero, features, $12.99 pricing, FAQ, CTA).          |
| `demo.html`     | Free limited demo — 3 categories, export/save locked.            |
| `planner.html`  | The full budget planner app (instructions + planner tabs).       |
| `netlify.toml`  | Netlify config: publish folder, friendly URLs, headers.           |
| `.gitignore`    | Keeps junk files out of the repo.                                 |
| `README.md`     | This file.                                                        |

The landing page's "Get it" buttons open the full planner; the "Try the live
demo" button opens `demo.html`. The demo runs the real planner with three
categories unlocked, while Excel export and save prompt visitors to buy. Every
"Unlock" / "Buy" button works the moment the site is live — see **Charging
$12.99** below to wire up real payment.

## Deploy to Netlify from GitHub

1. **Create a GitHub repo** and push these files to it:
   ```bash
   git init
   git add .
   git commit -m "Nursing budget planner site"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
   git push -u origin main
   ```

2. **Connect it to Netlify:**
   - Go to <https://app.netlify.com> and sign in.
   - Click **Add new site → Import an existing project**.
   - Choose **GitHub** and pick your repository.
   - Leave **Build command** empty and set **Publish directory** to `.`
     (Netlify reads `netlify.toml` and fills these in for you).
   - Click **Deploy**.

3. Netlify gives you a live URL like `your-site.netlify.app`. Every push to
   `main` redeploys automatically. Add a custom domain under
   **Site settings → Domain management** whenever you're ready.

## Charging $12.99 (optional)

The site ships with buttons that simply open the planner. To actually collect
$12.99, the easiest path is a **Stripe Payment Link**:

1. In Stripe, go to **Payment Links → New**, add a product priced **$12.99**,
   set it to a **one-time** payment.
2. Under the link's options, set the **success URL** to your planner page,
   e.g. `https://your-site.netlify.app/planner.html`.
3. Copy the payment link URL.
4. Open `index.html`, find this line near the bottom, and paste your link:
   ```js
   const CHECKOUT_URL = ""; // e.g. "https://buy.stripe.com/your_link"
   ```
   `demo.html` has the same `CHECKOUT_URL` line — paste your link there too so
   the demo's "Unlock" buttons go to checkout instead of the pricing section.
5. Commit and push. Every Buy button now sends people to Stripe, and Stripe
   returns paying customers to the planner.

> Note: a static site can't truly *lock* the planner behind payment on its own —
> anyone with the planner URL can open it. The Payment Link flow above is the
> common, low-friction approach for a one-time digital product. If you need a
> hard paywall, you'd add a small serverless function (Netlify Functions) to
> verify the Stripe session before serving the planner.

## Run it locally

Just open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## License

You own this copy — use and modify it freely.
