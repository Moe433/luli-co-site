# Luli Co. website — setup guide

One static site: `index.html` + `images` folder. No server, $0/month.

## 1. Push updates (you know this part)

```
git add .
git commit -m "your message"
git push
```

GitHub Pages rebuilds automatically within a minute or two of every push.

## 2. What changed in this rebuild

Full redesign — same content and working checkout, cleaner structure:
- Announcement bar + sticky nav with a working mobile hamburger menu (the old one just hid the nav on mobile with no replacement — that's fixed)
- Product section rebuilt as proper cards (image, name, price, color picker, pay button) in a responsive grid instead of the organic blob-shaped photo frames
- Trust strip under the hero (real flowers / free shipping / hand-checked / secure checkout)
- FAQ accordion (click to expand) combining clip care, checkout, color variation, and shipping — replaces the old static "Clip Care" grid
- Scroll-reveal animation on sections as you scroll down
- Same working PayPal checkout, color-swatch picker, and order-notification logic as before — nothing about how orders/payments work changed, just the surrounding design

## 3. Product photos

All 6 product photos were replaced with your real photos (AI-cleaned by you, then lightly sharpened/contrast-adjusted by me) — these are the actual product listing images:
- `product-floral-pair.jpg`
- `product-turtle-blue.jpg`, `product-turtle-brown.jpg`, `product-turtle-cream.jpg`, `product-turtle-green.jpg`
- `product-turtle-green-single.jpg`

The 8 `inspo-*.jpg` images stay in the "Styling Inspiration" gallery only — clearly labeled as mood photography, not product photos, so customers aren't misled about what ships.

## 4. Checkout — still needs one thing

PayPal Client ID is already wired in and working. The only remaining placeholder is the Formspree order-notification endpoint:

1. Free account at formspree.io → **"+ New Form"** → name it "Luli Co. Orders"
2. Copy the endpoint URL (looks like `https://formspree.io/f/abcdwxyz`)
3. In `index.html`, find `YOUR_FORMSPREE_ENDPOINT` and replace it
4. Push the update

Until that's set, checkout still works fine (PayPal takes payment either way) — you just won't get the itemized email/dashboard, only PayPal's own default payment notification.

## 5. Things you'll likely edit in index.html

- **Prices**: `16.99` / `14.99` / `9.99` — each appears in the visible price and in that product's `data-price` attribute, keep both in sync
- **Turtle duo colors/stock**: the 4 swatches under Turtle Duo Set have `data-color`, `data-stock`, `data-img` — edit as you sell through
- **FAQ answers**: plain text inside each `.faq-a-inner` div
- **Email**: `moerouk@gmail.com` throughout
- **TikTok**: already set to your real link

## 6. Inventory (as of this update)

- Turtle Duo Set: 5 each in Blue, Brown, Crème Peach, Green (20 total)
- Single Green Turtle Clip: 5
- Pressed Petal Clip Duo: 12

The defective blue clip and mismatched green pair are already excluded from these counts.