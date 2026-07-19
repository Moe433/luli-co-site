# Luli Co. website — setup guide

One static site: `index.html` + `images` folder. No server, $0/month.

## 1. Push updates (same as always)

```
git add .
git commit -m "your message"
git push
```

## 2. NEW: real cart system

This is the big change — checkout is no longer "pay per item." Now:
- Each product has an **"Add to bag"** button
- A cart icon in the top nav (with a live item count badge) opens a slide-in bag
- Customers can adjust quantity or remove items, see a running subtotal
- **One PayPal button at the bottom of the bag** checks out everything at once — a single payment, itemized in the description
- The bag is saved in the browser (survives a refresh) until they check out

Nothing else about how payment works changed — same PayPal Client ID, same Formspree notification logic, just now it fires once per full order instead of once per item.

## 3. NEW: hero photo

Replaced the single casual lineup shot with an editorial 3-photo collage (`images/hero-collage.jpg`) built from your real product photos — one large image plus two smaller ones, rounded corners, no fabricated content, just your real photos arranged more intentionally. If you don't like the specific crop/arrangement, say so and I'll rebuild it differently.

## 4. On the JS/CSS question

To be clear on what's actually in this file: custom cursor effect, scrolling marquee, hero parallax, scroll-reveal animations, drag-to-scroll gallery with progress bar, FAQ accordion, working mobile hamburger menu, and now the full cart system above — all hand-written CSS/JS in this one file, not a template or theme. If the live site isn't showing this, it's almost always a browser cache issue — hard refresh (Cmd+Shift+R / Ctrl+Shift+R) or check you're on the latest GitHub Pages deploy (Settings → Pages shows the last deploy time).

## 5. About that invoice PDF you sent

I pulled the embedded thumbnail photos out of it — they're small (240×240px to 350×278px) and would look soft/pixelated blown up to hero size, so I didn't use them directly. What was genuinely useful: the invoice's official item names don't quite match what the site currently calls them —

- Invoice says **"Pink turtle hair claw"** — the site currently calls this color "Crème Peach"
- Invoice says **"Light blue hair claw"** — the site currently calls this "Blue"
- Invoice says **"Dark green hair claw"** and **"Green hair claw"** as two distinct colors — the site currently only distinguishes "Green" and "Single Green"

Also worth flagging: the invoice only lists **small** claws (4.5×5.5cm) for Green, Pink, and Brown/leopard — not for Dark green or Light blue. So if the "Blue Turtle Duo" on the site is supposed to be a big+small pair, it's worth double-checking you actually have a small light-blue piece, since the invoice doesn't show one being ordered. I didn't change the color names or duo/single structure yet since this affects real inventory accuracy — let me know how you want to reconcile it and I'll update the site to match exactly.

## 6. Things you'll likely edit

- **Prices**: `16.99` / `14.99` / `9.99` in each `data-price` attribute
- **Turtle colors/stock**: `data-color`, `data-stock`, `data-img` on the 4 swatch buttons
- **FAQ answers**: plain text inside each `.faq-a-inner`