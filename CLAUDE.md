# PJA Carpentry Services — project memory

Static marketing site for PJA Carpentry Services (Paul Anderson), Gloucester.
Live at https://pjacs.co.uk via GitHub Pages. No build step: plain HTML, CSS
(`assets/css/style.css`), vanilla JS.

**Work directly on `claude/pauls-carpentry-website-flxsyt`.** That is the
branch GitHub Pages serves: push to it and the live site updates in ~2
minutes. Don't spread work across extra branches. If a session starts you on
its own branch, merge back to this one and delete the spare.

## Hard rules — never break these

- **No phone numbers anywhere** in text, links or code (`tel:` included).
  Contact is the form + paul@pjacs.co.uk only. Numbers visible inside photos
  (the van) are fine.
- **No street address anywhere.** Service area wording only: "Serving
  Gloucestershire, Cotswolds and Forest of Dean".
- **The email address never appears in the page source.** Don't write
  `mailto:paul@pjacs.co.uk` or the bare address into HTML, JSON-LD or
  `llms.txt`. Use `<a data-email href="contact.html">` (add
  `data-email-text` to show the address as the link text) and `main.js`
  builds it at runtime, so scrapers get nothing and non-JS visitors get
  the contact form.
- **The word "joinery"/"joiner" is banned.** The brand is exactly
  "PJA Carpentry Services".
- **Never call design work free.** Quotations are free; design and
  consultation are "included/part of the project".
- **No em/en dashes or AI-flavoured copy** anywhere on the site. No
  anthropomorphising, no AI tells, no brochure filler. Plain, confident,
  tradesman British English. Rewrites should sound like Paul. This is the
  site's voice and it is unaffected by the chat-tone rules further down.
- **Bathrooms are deliberately downplayed** (one mention inside Major
  Projects). Don't add bathroom sections or options without being asked.
- **No prices on the FAQ page (or anywhere else).** Every job is priced
  individually; the answer to cost questions is always the free,
  no obligation quotation. Keep `faq.html` copy and its FAQPage JSON-LD
  in sync if either changes.

## Who you are talking to (chat tone only)

This section governs how you write **replies in the Claude chat window**. It
has nothing to do with website copy. Never let it shorten, simplify or
otherwise influence what goes on the site: page copy is governed by the hard
rules above and by Positioning below.

Two people use this account. Work out which before you answer.

**Paul** (the owner, non-technical) is the default. Answers to Paul must be
short, sweet and really clear. A couple of sentences. Plain English, no
jargon, no git or branch talk, no headings and bullet lists unless he asks.
Tell him what changed and that the site will update itself. Never walk him
through technical options or ask him to make technical decisions. If
something needs a technical call, say it needs Mark.

**Mark** (his brother, built the site, technical) sometimes types on Paul's
account and will say so. With Mark: be direct and technical, give the detail,
skip the hand-holding.

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
- **Logo**: transparent PNGs in `assets/images/` — `logo.png` (navy, for
  light backgrounds, also referenced in the LocalBusiness schema) and
  `logo-footer.png` (white variant for the dark footer). Roofline mark
  with oak rafter, "BUILT AROUND YOU" tagline. Both variants supplied by
  Mark as transparent PNGs; ask him for matching artwork if it changes.
  Matching favicon set is done: `favicon.svg` (dark-mode aware),
  `favicon.ico` (16/32/48) and a 180px `apple-touch-icon.png`.
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
  records, and leave Google's site-verification TXT record alone too.
  Canonical domain is bare `pjacs.co.uk`.
- **Search Console**: verified as a Domain property via DNS under Paul's
  Google account (same account as GA4 and the Business Profile). No
  verification tag needed in the HTML.

## Docs in this repo

- `HANDOVER.md` — plain-English owner's guide for Paul
- `SETUP.md` — Analytics / Search Console / form / hosting setup
- `README.md` — technical overview and go-live checklist

## Open items

- A "kitchen brands" divider strip for the services page was designed but
  parked. Reviving it needs the actual brand logo files plus the brands
  Paul wants to list.
- Paul is a **sole trader**, not a limited company, so no registered
  company details are required in the footer. Settled, don't revisit.

Confirmed and closed: the "£2m public liability" figure and the old-site
Gloucester Kitchen Centre line are both verified by Paul and Mark (Sep
2026). GA4, Search Console, HTTPS, the contact form activation and the
favicon set are all done and live.

## Internal docs are not published

`_config.yml` excludes `CLAUDE.md`, `HANDOVER.md`, `README.md` and
`SETUP.md` from the GitHub Pages build, so they 404 on the live site
rather than being readable by crawlers. Any new internal doc must be added
to that exclude list.
