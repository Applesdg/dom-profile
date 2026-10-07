# Dominic – profile page

Static, self-contained site: `index.html` + `img/` (nebula background) + `photos/`. No CDN; the only third-party embed is the lazy-loaded Spotify player.
(`qr.js` is no longer loaded by the page; the on-page share section + QR were removed at Dom's request.)

## Add / reorder photos
1. Drop JPGs into `photos/` (portrait ~4:5, ~1080px wide is ideal).
2. Edit the `PHOTOS` array near the bottom of `index.html` (search "EDIT HERE ➜ PHOTOS").
   First entry = big hero photo; the rest fill the gallery in order. Optional `pos: "center 30%"` adjusts cropping.
3. Redeploy (static host = files must be re-uploaded):
   - GitHub Pages (stable URL, recommended): `/workspace/dom-profile-assets/deploy_github_pages.sh`
   - ShipStatic: `npx -y @shipstatic/ship ./dom-profile` (NOTE: every deploy gets a NEW url unless a domain is linked in a claimed account).

## Contact
Phone, Instagram, and SMS greeting live in the `CONTACT` object ("EDIT HERE ➜ CONTACT").
"Save my contact" builds a .vcf using the page's own URL (override with `SITE_URL`).

## Editable content (search "EDIT HERE" in index.html)
- `PHOTOS` – photo order + story captions (first = hero)
- `CONTACT` – phone / Instagram / SMS greeting
- `DATES` – first-date picker cards
- `QUIZ` / `QUIZ_LINES` – compatibility quiz questions + result lines
- Spotify track: `0JvUjekRwmDcQq4S0Sxocf` (Drew Barrymore, Bryce Vine) in the anthem section

## QR / cards
`python3 /workspace/dom-profile-assets/make_qr.py <URL>` regenerates qr.png/svg, card.png/pdf, and the 10-up Letter sheet in `/workspace/dom-profile-assets/print/`.
