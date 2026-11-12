# Mountaineer Vehicle Shipping

Homepage for Mountaineer Vehicle Shipping. A single static page: `index.html` plus `logo.png`.

The instant-quote form in the hero is the Ship Guy plug-and-play pricing tool, pasted into `index.html`.
It posts leads to `/api/quote/*`, which `functions/api/quote/[[path]].js` forwards to BeRocker using this
site's Lead Source key. That function is a Cloudflare Pages Function, so the quote form only works when the
site is hosted on Cloudflare Pages (or the same proxy is recreated on another serverless host).

To add the tool to another page, paste the same block (one per page) and keep its `PQ_CONFIG` values in sync.

## Before going live

Replace the bracketed placeholders in `index.html`:

- `siteUrl` / `siteLabel` in `PQ_CONFIG` (`[YOUR DOMAIN]`)
- Add this site's domain to the Google Maps key's referrer restrictions (ZIP suggestions)
- `[EMAIL ADDRESS]` / `mailto:[EMAIL]` and `[HOURS]`
- `[USDOT #]` and `[MC #]`
- `[RATING]`, `[NUMBER]` and the three customer review cards
- `[YOUR DEPOSIT AND PAYMENT POLICY]` in the FAQ
- The Privacy, Terms and Licensing & Insurance footer links

## Hosting

Cloudflare Pages, with this repo as the source and no build step. The Lead Source key can be moved out of the
function file into the `BEROCKER_LEAD_KEY` environment variable.
