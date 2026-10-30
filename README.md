# Tailored Furniture website

One-page site for Tailored Furniture (custom furniture, Filipino-owned since 1995). Everything in this repo is published, so `img/res-living.webp` is live at `<site address>/img/res-living.webp`.

## Files

| File / folder | What it is |
|---|---|
| `index.html` | The whole page: styles, content and scripts |
| `site-config.js` | Where form requests are emailed (Formspree ID or Web3Forms key) |
| `img/` | Photos and logos |
| `media/` | Hero film: `hero-1080-lite.mp4` (large screens), `hero-720.mp4` (laptops), `hero-portrait.mp4` (phones), `.webm` fallbacks, `hero-poster.webp` (first frame, shown while the film loads) |
| `docs/` | Company profile PDF (hero download button). Keep the file name; to update it, upload a new PDF under the same name, ideally under 5 MB |
| `404.html` | Page shown for a wrong address |
| `CNAME` | Added when the custom domain is connected |

## Requests (leads)

Every form on the page (room blueprint, Trade Program, cost per seat, office visit, worth-saving check, swatch box, consultation) emails one plain-text request to the inbox set in the form service. Photos are not attached: the confirmation screen asks the visitor to send them on Viber.

To change where requests go, change the email in the Formspree (or Web3Forms) dashboard. No code change needed.

## Hero film rules

- Keep the film files under the names above; the page picks one per screen size.
- New film: encode H.264 (no audio, 30 fps, `-movflags +faststart`) at 1920x1080 (~4 Mbps), 1280x720 (~2 Mbps) and a 540x960 centre crop for phones, plus matching WebM files, and replace `hero-poster.webp` with the new first frame.
- Update the "Now showing" timings (`const CHAPTERS`) in `index.html` if the scenes change.

## Placeholders to confirm with the client

Search `index.html` for these before launch: the Fit Guarantee, "We draw 10 room blueprints a week", the Christmas order line, the Trade Program perks, the 3-working-day blueprint turnaround (`RULES`), service areas, call times, and the example prices in the cost-per-seat and worth-saving tools.
