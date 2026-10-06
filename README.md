# Dominic – profile page

Static, self-contained site: `index.html` + `qr.js` (local QR generator, MIT) + `photos/`. No CDN.

## Add / reorder photos
1. Drop JPGs into `photos/` (portrait ~4:5, ~1080px wide is ideal).
2. Edit the `PHOTOS` array near the bottom of `index.html` (search "EDIT HERE ➜ PHOTOS").
   First entry = big hero photo; the rest fill the gallery in order. Optional `pos: "center 30%"` adjusts cropping.
3. Redeploy (static host = files must be re-uploaded):
   - GitHub Pages (stable URL, recommended): `/workspace/dom-profile-assets/deploy_github_pages.sh`
   - ShipStatic: `npx -y @shipstatic/ship ./dom-profile` (NOTE: every deploy gets a NEW url unless a domain is linked in a claimed account).

## Contact / share
Phone, Instagram, and SMS greeting live in the `CONTACT` object ("EDIT HERE ➜ CONTACT").
Share button uses the Web Share API (AirDrop on iPhone, Quick Share on Android), with copy-link fallback.
The inline QR and the vCard use the page's own URL automatically (override with `SITE_URL`).

## QR / cards
`python3 /workspace/dom-profile-assets/make_qr.py <URL>` regenerates qr.png/svg, card.png/pdf, and the 10-up Letter sheet in `/workspace/dom-profile-assets/print/`.
