# Dominic – profile page

Static, self-contained site: `index.html` + `img/` (nebula background) + `photos/` + `vendor/leaflet/`. No CDN; third-party requests are only the lazy-loaded Spotify player and OpenStreetMap map tiles.

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
- `THIS_OR_THAT` – "This or that" rounds: options, my pick (`dom`), and the witty reply for each answer (`say`). `READ_MS` sets how long each reply stays up.
- Spotify track: `0JvUjekRwmDcQq4S0Sxocf` (Drew Barrymore, Bryce Vine) in the anthem section
- `ASK_BENJI` – "Ask Benji" preset questions + Benji's answers (optional `sms` adds a Text button)
- `MAP_SPOTS` – Space Coast date map pins (name, lat/lng, emoji, one-line idea): Del's Freez, Brevard Zoo, Canova Dog Beach, Wickham Park, Kennedy Space Center.
  The map zooms to fit all pins automatically.
  Get lat/lng by right-clicking a spot in Google Maps and clicking the coordinates to copy them.
- Green/red flags are plain HTML in the `#flags` section.
- `VOICE_INTRO` – see below.
- `CURRENTLY` – the "● Currently: …" status pill under the hero chips. It's the first line of the main script:
  `const CURRENTLY = 'at the gym 💪';` – change the text (emoji welcome), or set it to `''` to hide the pill.
  (Also update the fallback text in `<span id="now-txt">` if you want visitors without JavaScript to see the same thing.)

## Voice intro ("Hear me say hi")
The button is hidden until you turn it on:
1. Record a short hello and save it as `audio/hi.mp3` (keep it small, ~10 s).
2. In `index.html`, change `const VOICE_INTRO = "";` to `const VOICE_INTRO = "audio/hi.mp3";`
3. Commit + push. (If the line is set but the file is missing, the button stays hidden.)

## Map
Leaflet 1.9.4 is vendored in `vendor/leaflet/` (no CDN, no API key); tiles come from OpenStreetMap
(attribution shown on the map). On phones one finger scrolls the page and pinch zooms the map;
"Tap to move map" enables one-finger dragging. Scroll-wheel zoom is off so the page never gets stuck.

## Easter egg
Tapping the background (not a card/button) 5 times within ~4 s opens a secret "stardust" overlay. No hint on the page.

## QR / cards
`python3 /workspace/dom-profile-assets/make_qr.py <URL>` regenerates qr.png/svg, card.png/pdf, and the 10-up Letter sheet in `/workspace/dom-profile-assets/print/`.
