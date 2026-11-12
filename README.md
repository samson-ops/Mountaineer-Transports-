# Mountaineer Vehicle Shipping

Static website for Mountaineer Vehicle Shipping. No build step: plain HTML pages, one shared `styles.css`, and `logo.png`.

## Pages

- `/` — homepage
- `/how-it-works/`, `/car-shipping-cost/`, `/preparation-checklist/`, `/cross-country-shipping/`
- `/services/` and one page each for open, enclosed, door-to-door, state-to-state, expedited, snowbird, military and auction transport
- `/faq/`, `/reviews/`, `/contact/`
- `/licensing-insurance/`, `/privacy/`, `/terms/`
- `404.html`

City and state pages are not included.

## Pricing tool

Every page except Privacy, Terms and the 404 page carries the Ship Guy plug-and-play pricing tool in its hero
(one per page, pasted unchanged apart from `PQ_CONFIG`). It posts leads to `/api/quote/*`, which
`functions/api/quote/[[path]].js` forwards to BeRocker using this site's Lead Source key. That file is a
Cloudflare Pages Function, so the quote form only works when the site is hosted on Cloudflare Pages
(or the same proxy is recreated on another serverless host).

The `PQ_CONFIG` block is repeated on each page that has the tool. Change it everywhere at once.

## Before going live

Search the repo for `[` to find the placeholders still to fill in:

- `[EMAIL ADDRESS]` / `mailto:[EMAIL]`, `[HOURS]`, `[MAILING ADDRESS]`
- `[USDOT #]`, `[MC #]`, `[LEGAL ENTITY NAME]`
- `[RATING]`, `[NUMBER]`, `[GOOGLE REVIEWS LINK]` and the customer review cards
- Deposit, payment, cancellation, military discount and claims policies
- `[EFFECTIVE DATE]`, `[STATE]` and the other bracketed terms in Privacy and Terms (have a lawyer review both pages)
- `siteLabel` in `PQ_CONFIG` (`[YOUR DOMAIN]`)
- Add this site's domain to the Google Maps key's referrer restrictions (ZIP suggestions)

## Hosting

Cloudflare Pages, with this repo as the source and no build command. The Lead Source key can be moved out of
the function file into the `BEROCKER_LEAD_KEY` environment variable.
