# Setup guide — analytics, Site Kit, contact form, hosting

**Status: setup is complete.** Analytics, Search Console, the contact form
and HTTPS hosting are all live. This file is kept as reference for how each
piece was wired up and what to do if one ever needs redoing.

## 1. Google Analytics 4 — DONE

Live with Measurement ID `G-L3VBRE5JH5` in `assets/js/consent.js`, under
Paul's Google account. He can see the numbers in the Google Analytics app.
The original setup steps follow, for reference only.

1. Go to [analytics.google.com](https://analytics.google.com) and sign in with
   the Google account that should own the data (Paul's ideally).
2. **Admin → Create → Property** — name it "PJA Carpentry Services", country
   United Kingdom, currency GBP.
3. Add a **Web data stream** for `https://pjacs.co.uk` and copy the
   **Measurement ID** (looks like `G-ABC123XYZ`).
4. Open `assets/js/consent.js` and replace:

   ```js
   var GA_MEASUREMENT_ID = "G-XXXXXXXXXX";
   ```

   with the real ID. That's it — the site already includes the gtag snippet,
   Consent Mode v2, IP anonymisation, and a `generate_lead` event fired on
   contact-form submission.

> **Privacy note:** analytics only loads after a visitor clicks "Accept
> analytics" in the cookie banner. This is required under UK GDPR/PECR — don't
> bypass it.

## 2. Google Search Console — DONE

Verified as a **Domain property** for `pjacs.co.uk` via a DNS TXT record at
IONOS (added automatically through Domain Connect), under Paul's Google
account. No verification tag lives in the HTML. Do not remove the
`google-site-verification` TXT record from the IONOS DNS.

Sitemap: `https://pjacs.co.uk/sitemap.xml` — submit/re-check it under
**Sitemaps** in Search Console.

## 3. Google Site Kit

Site Kit is Google's **WordPress plugin** — it can't run on a static site like
this one, and it isn't needed: this site already wires up everything Site Kit
would (Analytics tag + Search Console verification, steps 1–2 above).

If the site is ever moved onto WordPress, install **Site Kit by Google** from
the plugin directory, click "Start setup", and connect Search Console and
Analytics with the same Google account as above — then remove the hand-rolled
gtag code so it isn't counted twice.

## 4. Contact form (FormSubmit → paul@pjacs.co.uk) — DONE

The form in `contact.html` posts to FormSubmit, a free relay service that
emails each submission; no server code needed.

**Activation is complete** and enquiries are being delivered. Nothing to do
unless the destination address ever changes, in which case the new address
needs activating the same way (first submission triggers a confirm email).

**Optional hardening (recommended):** after activation, FormSubmit's email
shows a random alias for the address (like `formsubmit.co/a1b2c3d4...`).
Swap the form's `action` to that alias so the email address never appears in
the page source — one small edit in `contact.html`.

The form already includes a honeypot field for spam bots, a GDPR consent
checkbox, and redirects to `thanks.html` after sending (the `_next` hidden
field — update it if the domain ever changes).

**Alternative:** if you'd rather use Formspree, create a form at
[formspree.io](https://formspree.io) pointing at paul@pjacs.co.uk and change
the form `action` to the endpoint they give you. Nothing else needs to change.

## 5. Hosting & HTTPS — DONE

Live on **GitHub Pages**, served from the
`claude/pauls-carpentry-website-flxsyt` branch with `pjacs.co.uk` as the
custom domain (see the `CNAME` file). DNS is at IONOS: four `A` records for
the apex plus the `www` CNAME. "Enforce HTTPS" is on, so certificates are
issued and renewed automatically.

## 6. Keeping internal docs off the live site

GitHub Pages serves every file on the branch, so `CLAUDE.md` and the other
markdown docs were originally fetchable at `pjacs.co.uk/CLAUDE.md`.
`_config.yml` now excludes them from the Jekyll build and they return 404.
**Any new internal doc must be added to that exclude list**, or it will be
published and crawlable.
