# Luli Co. website — setup guide

One static site: `index.html` + `images` folder. No server, $0/month.

## 1. Push updates (same as always)

```
git add .
git commit -m "your message"
git push
```

## 2. What's new in this version

Full visual rebuild, same working checkout underneath:
- **Scrolling marquee ticker** under the top nav (real flowers / free shipping / etc.)
- **Bigger, bolder hero** with floating annotation cards and a subtle parallax effect on the photo as you scroll
- **Magnetic cursor dot** on desktop that reacts near clickable elements
- **Product cards rebuilt** with hover image zoom and lift
- **New pull-quote/stat section** between Shop and Our Story
- **Inspiration gallery rebuilt** as a horizontal drag-to-scroll gallery (click and drag, or use the arrow buttons) with a progress bar, instead of a static stacked grid
- **FAQ accordion**, working mobile hamburger menu — unchanged from before, still here
- Subtle background grain texture for a less "flat" feel

Checkout, color picker, PayPal Client ID, and order-notification logic are all unchanged — this was a design pass, not a functionality change.

## 3. Product photos

All 6 product photos are your real photos (AI-cleaned by you, lightly sharpened by me):
`product-floral-pair.jpg`, `product-turtle-blue.jpg`, `product-turtle-brown.jpg`, `product-turtle-cream.jpg`, `product-turtle-green.jpg`, `product-turtle-green-single.jpg`

The 8 `inspo-*.jpg` images are AI-generated lifestyle/mood shots — they only appear in the "Styling Inspiration" gallery, clearly labeled as not literal product photos.

## 4. Checkout — still needs one thing

PayPal Client ID is wired in and working. Formspree (the itemized order-notification email) is still a placeholder:

1. Free account at formspree.io → "+ New Form" → name it "Luli Co. Orders"
2. Copy the endpoint (`https://formspree.io/f/abcdwxyz`)
3. In `index.html`, replace `YOUR_FORMSPREE_ENDPOINT` with it
4. Push

Until then, checkout still works — PayPal's own default payment notification still reaches you either way.

## 5. Things you'll likely edit

- **Prices**: `16.99` / `14.99` / `9.99`, each appears in the visible price and that product's `data-price` attribute
- **Turtle colors/stock**: `data-color`, `data-stock`, `data-img` on the 4 swatch buttons
- **FAQ answers**: plain text inside each `.faq-a-inner`
- **Stat numbers** in the pull-quote section (`100%`, `5`, `1/1`) — update if your actual color count changes

## 6. Inventory (as of this update)

- Turtle Duo Set: 5 each in Blue, Brown, Crème Peach, Green (20 total)
- Single Green Turtle Clip: 5
- Pressed Petal Clip Duo: 12