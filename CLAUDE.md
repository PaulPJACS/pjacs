# PJA Carpentry Services — project memory

Static marketing site for PJA Carpentry Services (Paul Anderson), Gloucester.
Live at https://pjacs.co.uk via GitHub Pages. No build step: plain HTML, CSS
(`assets/css/style.css`), vanilla JS. Push to the deployed branch and the live
site updates in ~2 minutes.

## Hard rules — never break these

- **No phone numbers anywhere** in text, links or code (`tel:` included).
  Contact is the form + paul@pjacs.co.uk only. Numbers visible inside photos
  (the van) are fine.
- **No street address anywhere.** Service area wording only: "Serving
  Gloucestershire, Cotswolds and Forest of Dean".
- **The word "joinery"/"joiner" is banned.** The brand is exactly
  "PJA Carpentry Services".
- **Never call design work free.** Quotations are free; design and
  consultation are "included/part of the project".
- **No em/en dashes or AI-flavoured copy.** Plain, confident, tradesman
  British English. Rewrites should sound like Paul, not a brochure.
- **Bathrooms are deliberately downplayed** (one mention inside Major
  Projects). Don't add bathroom sections or options without being asked.

## Positioning

Kitchens first, fitted bedrooms second, then bespoke carpentry, major
projects and property maintenance. One-stop shop for whole-home improvement.
High-end, big jobs. Key claims in use: "rated by his clients as the best
kitchen fitter in Gloucester", 30+ years, 5.0 on Google (17 reviews —
update the number occasionally), Featured on the Best of Gloucester,
£2m public liability, family run since 2010.

## How things work

- **Analytics**: GA4 ID `G-L3VBRE5JH5` lives in `assets/js/consent.js`.
  Consent-gated (UK GDPR) — never load it before the banner is accepted.
- **Contact form**: posts to FormSubmit → paul@pjacs.co.uk, honeypot +
  consent tick, redirects to `thanks.html`.
- **Logo**: inline SVG roofline mark (in every page header/footer),
  modernised from the van livery. Favicon set matches.
- **Images**: optimise before adding (max 1600px, progressive JPEG, ~80
  quality, EXIF rotation applied). Project photos live in `assets/images/`
  and `assets/images/latest/`.
- **Latest work**: homepage gallery of thumbnails linking to `work-*.html`
  project pages (one page per project; multi-angle shots share a page).
  New pages follow the same template; add them to `sitemap.xml`.
- **Google profile**: https://maps.app.goo.gl/LNscLGL3hLSvfuHW8
  **Facebook**: facebook.com/100062215727083 (click-to-load embed on
  Testimonials — keep it consent-safe).
- **Domain/DNS**: IONOS holds DNS (4 × A records to GitHub Pages IPs, www
  CNAME). Mail (MX/SPF/DKIM/DMARC) is IONOS mail — never touch those
  records. Canonical domain is bare `pjacs.co.uk`.

## Docs in this repo

- `HANDOVER.md` — plain-English owner's guide for Paul
- `SETUP.md` — Analytics / Search Console / form / hosting setup
- `README.md` — technical overview and go-live checklist

## Open items

- Search Console verification token still to be added to `index.html`
  (placeholder comment in the `<head>`).
- Confirm the "£2m public liability" figure and the old-site line about
  the Gloucester Kitchen Centre with Paul.
- A "kitchen brands" divider strip for the services page was designed but
  parked — real brand logos needed if revived.
