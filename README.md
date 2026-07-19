# Luli Co. website — setup guide

One static site: `index.html` + `images` folder. No server, $0/month.

## 1. Deploy from VS Code (git push → GitHub Pages)

1. Open this folder in VS Code
2. Terminal:
   ```
   git init
   git add .
   git commit -m "Launch Luli Co. site"
   ```
3. Create a new empty repo on github.com — copy the repo URL
4. Back in the terminal:
   ```
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
   git branch -M main
   git push -u origin main
   ```
   (Or use VS Code's Source Control panel — stage all, commit, "Publish Branch" does the same thing.)
5. On github.com → repo → **Settings → Pages** → Source: **Deploy from a branch** → `main` / `/ (root)` → Save
6. Live in a minute or two at `https://YOUR-USERNAME.github.io/YOUR-REPO/`

Future updates: edit → `git add .` → `git commit -m "update"` → `git push`.

## 2. How checkout works now (one step, nothing for the customer to fill out separately)

The "Pay" buttons are PayPal's own embedded checkout — right on the page, no redirect. When someone buys, PayPal itself asks them for their shipping address as a normal part of paying for a physical item — that's standard, nothing you need to configure.

The moment a payment succeeds, the page silently sends you a clean order notification in the background (item, buyer name/email, full shipping address) — the customer never sees this happen, there's no second form.

**You're already getting notified today, for free, with zero setup** — PayPal automatically emails you (and shows it in your PayPal app/account) every time you receive a payment. Everything below just adds a tidier, itemized version of that alongside it, plus a running dashboard of orders.

### Setup — one thing left to paste into `index.html`

**A. PayPal Client ID — already done ✓**
Your real Client ID is already in the file.

**B. Formspree endpoint** (turns the background order data into an email + dashboard)
1. Create a free account at formspree.io
2. Click **"+ New Form"**, name it "Luli Co. Orders"
3. Copy the endpoint URL it gives you — looks like `https://formspree.io/f/abcdwxyz`
4. In `index.html`, find `YOUR_FORMSPREE_ENDPOINT` and replace it with your real endpoint
5. Free tier covers 50 orders/month — plenty to start; it'll prompt you to upgrade if you outgrow that (good problem to have)

Once that's in, redeploy (git add/commit/push) and you're live: customer pays in one step, you get an email with their name/address/item/color, and every order also lands in your Formspree dashboard as a running list — that's your "stay on top of everything" view without needing to build anything else.

### A note on stock

This setup doesn't auto-track remaining inventory (that needs a real database, which starts costing money). At your current scale, the simplest free approach is just glancing at your own physical stock after each order comes in via email — if you outgrow that, a lightweight spreadsheet you update by hand after each Formspree notification works fine too.

## 3. Payments — what customers can pay with

PayPal's embedded checkout already accepts a PayPal balance, linked bank, or debit/credit card as a guest — nothing extra to turn on. No monthly fee, PayPal just takes their standard % per transaction.

**Apple Pay / Google Pay as dedicated buttons** (instead of a card option inside PayPal checkout) needs PayPal's bigger "Advanced Checkout" integration with domain verification — still free, just more setup. Worth doing once you're live and selling: https://developer.paypal.com/docs/checkout/apm/apple-pay/

## 4. Things you'll likely edit in index.html

- **Prices**: `16.99` (floral duo), `14.99` (turtle duo), `9.99` (single turtle) — each appears in the visible price and in that product's `data-price` attribute — keep both in sync
- **Turtle duo colors/stock**: the 4 color swatches under Turtle Duo Set each have `data-color`, `data-stock`, and `data-img` attributes — edit stock numbers there as you sell through
- **TikTok**: already set to your real link
- **Product copy**: text inside `<h3>`, `<p class="desc">`, and `<li>` tags for each product
- **Email**: already set to `moerouk@gmail.com` throughout

## 5. Inventory note (as of this update)

- Turtle Duo Set: 5 each in Blue, Brown, Crème Peach, Green (20 total)
- Single Green Turtle Clip: 5
- Pressed Petal Clip Duo: 12

The defective blue clip and mismatched green pair are already excluded from these counts — being set aside as gifts, not sold. Update the numbers above (and the matching `data-stock` values in `index.html`) as orders come in.

## 6. About the current photos

All 6 product photos have the background removed and replaced with a clean, uniform off-white — no more carpet/room visible. Filenames are unchanged from before, so this was a drop-in image swap with no HTML edits needed:
- `product-floral-pair.jpg`, `product-turtle-blue.jpg` — sourced from the cleaner factory delivery photos, these came out the cleanest
- `product-turtle-cream.jpg`, `product-turtle-green.jpg`, `product-turtle-green-single.jpg` — sourced from your at-home photos, reworked with a stronger cutout technique (2nd pass) — should look meaningfully better than the first attempt
- `product-turtle-brown.jpg` — same 2nd-pass technique, but this one's leopard-print pattern is the hardest case (lots of internal color contrast confuses the cutout). Check this one first — if it's still rough, the real fix is a photo on an actual plain white/light background (printer paper or poster board behind the product) rather than another automated attempt, since carpet is fundamentally a hard background to cut cleanly without a proper AI segmentation model, which isn't available in this environment.

## 7. Styling inspiration gallery

Added a new section between "Our Story" and "Clip Care" — 8 mood/lifestyle photos (`images/inspo-1.jpg` through `inspo-8.jpg`) showing the aesthetic direction, NOT claimed as literal photos of your inventory. There's a small disclosure line under the gallery ("Mood photography for styling inspiration — see the product listings above for real photos of exactly what ships") so customers aren't misled about what they're actually buying — the real product photos stay on the product listings themselves, untouched.