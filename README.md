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

Requests are delivered by FormSubmit (formsubmit.co) to the email in `site-config.js` (currently tailoredfurnph@gmail.com, the address in the company profile). FormSubmit needs a one-time activation: the first request sends an "Activate Form" email to that inbox, and nothing is delivered until someone clicks it. To change the inbox, change `formsubmit` in `site-config.js` and activate again from the new inbox.

## Hero film rules

- Keep the film files under the names above; the page picks one per screen size.
- New film: encode H.264 (no audio, 30 fps, `-movflags +faststart`) at 1920x1080 (~4 Mbps), 1280x720 (~2 Mbps) and a 540x960 centre crop for phones, plus matching WebM files, and replace `hero-poster.webp` with the new first frame.
- Update the "Now showing" timings (`const CHAPTERS`) in `index.html` if the scenes change.

## Placeholders to confirm with the client

Search `index.html` for these before launch: the Fit Guarantee, the Trade Program perks, the 3-working-day blueprint turnaround (`RULES`), service areas, call times, and the example prices in the cost-per-seat and worth-saving tools.

## Domain and hosting

- Live at **https://tailoredfurn.com/** (GitHub Pages, set by the `CNAME` file). `www.tailoredfurn.com` redirects to it.
- DNS is in Cloudflare (DNS only, grey cloud): four `A` and four `AAAA` records for `@` pointing to GitHub Pages, and `www` as a `CNAME` to `cristycussolutions.github.io`. HTTPS certificate is issued by GitHub; "Enforce HTTPS" is on in Settings, Pages.
- Email safety: the domain does not send email, so it has `v=spf1 -all` and a `p=reject` DMARC record. If you ever set up email on tailoredfurn.com, replace both first.

## Search and sharing

- `sitemap.xml` and `robots.txt` (update `lastmod` in the sitemap when content changes)
- Business details for Google live in the `application/ld+json` block in `index.html` (name, phone, email, service area, services). Add a street address there once the business has a public one.
- `llms.txt`: plain facts for AI assistants. Keep it in step with the page.
- `og-image.jpg` (1200x630): the picture shown when the link is shared.
