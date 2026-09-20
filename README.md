# PJA Carpentry Services — website

A modern, fast, fully static website for PJA Carpentry Services (Paul Anderson),
Gloucester — rebuilt in 2026 from the previous pjacs.co.uk site.

No build step, no frameworks, no database: plain HTML + CSS + a little vanilla
JavaScript. Upload the files to any web host (or serve via GitHub Pages) and it
works.

## Pages

| File | Purpose |
|---|---|
| `index.html` | Home — hero, services overview, featured work, testimonials |
| `services.html` | Kitchens, bedrooms, bespoke carpentry, major projects, maintenance |
| `portfolio.html` | Filterable gallery of real project photos with lightbox |
| `testimonials.html` | 16 genuine client testimonials, Google reviews and a click-to-load Facebook embed |
| `about.html` | Paul's background, values, service area |
| `faq.html` | Common questions, with FAQPage structured data. No prices |
| `contact.html` | Contact form (delivers to paul@pjacs.co.uk) |
| `work-*.html` | Ten project pages, one per job, linked from the homepage gallery |
| `review.html` | Redirect to the Google review page, for the QR code sticker |
| `privacy.html` / `cookies.html` | UK GDPR privacy policy & cookie policy |
| `thanks.html` | Post-submission thank-you page |
| `404.html` | Not-found page |

Assets live in `assets/` (css, js, images). All project photos were taken from
the previous site, rotation-corrected and optimised for the web (max 1600 px,
progressive JPEG).

## Go-live — complete

The site is live at https://pjacs.co.uk. Everything on the original launch
checklist is done:

1. **Google Analytics** — live, ID `G-L3VBRE5JH5` in `assets/js/consent.js`,
   consent-gated as UK law requires.
2. **Contact form** — FormSubmit activated, enquiries delivering to
   `paul@pjacs.co.uk`.
3. **HTTPS** — GitHub Pages with Enforce HTTPS on; certificates auto-renew.
4. **Details verified** — "30+ years", "£2m public liability", founding year
   2010 and the Gloucester Kitchen Centre line are all confirmed. Phone
   numbers and the street address are deliberately absent; contact is the
   form plus email.
5. **Company details** — Paul is a sole trader, so no registered company
   details are required in the footer.
6. **Search Console** — verified as a Domain property via DNS. See
   `SETUP.md`.

Note that `_config.yml` keeps this file and the other internal docs out of
the published site. Add any new internal doc to its exclude list.

## Editing tips

- The gallery is a plain list of `<figure class="work-item">` blocks in
  `portfolio.html` — copy one, set `data-category`, drop a new optimised photo
  into `assets/images/`, done.
- Testimonials are `<article class="quote-card">` blocks — add freely.
