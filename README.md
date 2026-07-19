# Luli Co. website — setup guide

One static site: `index.html` + `images` folder. No server, $0/month.

## 1. Push updates (same as always)

```
git add .
git commit -m "your message"
git push
```

## 2. What changed this round (from the ChatGPT feedback pass)

**Implemented:**
- Hero headline rewritten to lead with the product ("Hair clips made with real flowers")
- Quick-add "+" button appears on hover over each product photo (always visible on mobile/touch), triggers the same add-to-bag logic as the main button
- "Our Story" headline softened
- Stock counts now styled in gold as a scarcity cue ("Only 12 left this batch", etc.) — numbers are still your real inventory, just styled to stand out
- New "Follow the making process" section linking to TikTok, moved higher up the page (right after the Shop section)
- New "gift from nature" section (birthdays / bridesmaids / Mother's Day / self-care)
- Favicon added (`images/favicon-32.png`, `images/favicon-180.png`, generated from your logo)
- Announcement bar copy tightened

**Deliberately NOT implemented — fabricated reviews.** The suggestion was to add fake testimonials attributed to made-up customers (e.g. `"Beautiful clip!" — Sarah`). That's not a design choice, it's a fabricated endorsement, and it's the kind of thing the FTC has gone after small brands for. Instead there's an honest placeholder section ("Be the first to leave one") that invites real customers to send a photo once you have actual orders — swap it out for genuine reviews as they come in.

**Also clarified, not a real issue:** your PayPal Client ID being visible in the page source is normal and expected — Client IDs (unlike Secrets) are meant to be public, that's how the PayPal JS SDK always works. Nothing to fix there.

## 3. Still outstanding (real-world, not code)

- **Product photography**: the feedback about close-ups, worn shots, and hand-for-scale photos is genuinely good advice, but it needs an actual camera and your actual product — not something I can generate. Worth doing once you have a slow afternoon.
- **Formspree endpoint**: still a placeholder (`YOUR_FORMSPREE_ENDPOINT`) — orders won't email you until this is set. Steps are in section 4 below.

## 4. Checkout — still needs one thing

PayPal Client ID is wired in and working (cart system, single checkout). Formspree (the itemized order-notification email) is still a placeholder:

1. Free account at formspree.io → "+ New Form" → name it "Luli Co. Orders"
2. Copy the endpoint (`https://formspree.io/f/abcdwxyz`)
3. In `index.html`, replace `YOUR_FORMSPREE_ENDPOINT` with it
4. Push

## 5. Things you'll likely edit

- **Prices**: `16.99` / `14.99` / `9.99` in each `data-price` attribute
- **Turtle colors/stock**: `data-color`, `data-stock`, `data-img` on the 4 swatch buttons — also update the matching `scarcity` text near each price
- **FAQ answers**: plain text inside each `.faq-a-inner`
- **Reviews section**: swap the placeholder copy for real reviews once you have them