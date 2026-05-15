# Deploy Tantra Authority to Cloudflare Pages

The fastest path. ~3 minutes once your DNS is already at Cloudflare (which yours is).

---

## Option A — Direct upload (fastest, no git required)

1. Log into Cloudflare dashboard → **Pages** (left sidebar) → **Create a project** → **Upload assets**
2. Drag this entire `tantra-authority/` folder onto the upload area
3. Cloudflare assigns it a `*.pages.dev` URL automatically (e.g. `tantra-authority.pages.dev`)
4. Verify it works at that URL
5. **Add custom domain** → enter `tantraauthority.com` → Cloudflare auto-creates the DNS record (since the domain is already in your Cloudflare account)
6. Done. SSL auto-provisions in ~60 seconds.

**Cost:** $0/month at any traffic level under 100k requests/day (free tier is generous).

---

## Option B — Git-connected (recommended for ongoing updates)

This makes every `git push` auto-deploy, same model as the BTC-rings GitHub Pages setup.

### One-time setup

```bash
cd /Users/lawgreg/consciousness_agent/code/verticals/tantra-authority
git init
git add .
git commit -m "Tantra Authority — initial scaffold"
gh repo create tantra-authority --public --source=. --push
```

Then in Cloudflare dashboard:

1. **Pages** → **Create a project** → **Connect to Git**
2. Select the `tantra-authority` repo
3. Build settings:
   - **Build command:** *(leave blank — pure static HTML, no build step)*
   - **Build output directory:** `/` *(root)*
4. **Deploy**
5. Add custom domain (`tantraauthority.com`) under the project settings

Every `git push origin main` will trigger a deploy after this.

### To add articles or update content later

```bash
cd /Users/lawgreg/consciousness_agent/code/verticals/tantra-authority
# edit/add HTML files
git add .
git commit -m "New article: X"
git push
```

Live in ~30-60 seconds.

---

## Custom domain: `tantraauthority.com` AND `tantra-authority.com`

You own both. Recommended: point both at the same Cloudflare Pages project.

- Primary: `tantraauthority.com` (the canonical)
- Redirect: `tantra-authority.com` → `tantraauthority.com` (set up a Page Rule in Cloudflare, free)

This avoids duplicate-content SEO penalty while preserving both domains' value.

---

## Per-vertical template — replicating this for the next 9 sites

This directory IS the template. To spin up the next vertical (e.g. The Open Relationship Blueprint):

```bash
cp -r /Users/lawgreg/consciousness_agent/code/verticals/tantra-authority \
      /Users/lawgreg/consciousness_agent/code/verticals/open-relationship-blueprint
cd /Users/lawgreg/consciousness_agent/code/verticals/open-relationship-blueprint
# rm articles/* (start fresh)
# edit index.html, book.html, about.html — swap topic/brand
# write new articles
git init && git add . && git commit -m "ORB site — initial scaffold"
gh repo create open-relationship-blueprint --public --source=. --push
# Connect in Cloudflare Pages, point theopenrelationshipblueprint.com at it
```

Each vertical = ~30 min to spin up once the template is solid.

---

## Newsletter / form wiring

Right now the email signup forms in `index.html`, `book.html`, and any article use a placeholder `onsubmit` that just shows an alert. To make them real:

**Option 1 — Substack:** point form `action` at `https://thenakedmind.substack.com/api/v1/free?nojs=true`, posting `email`. Subscribes them to The Naked Mind directly.

**Option 2 — ConvertKit:** standard form embed. Replace the form HTML with their copy/paste embed code.

**Option 3 — Buttondown:** similar embed pattern. Cheaper than ConvertKit at scale.

**Option 4 — Custom (when you're ready):** Cloudflare Workers can handle form submission and route to ConvertKit / Mailchimp / wherever via their API. About 30 lines of code.

Recommend: start with **Substack** so signups go directly into The Naked Mind list. Single list, single brand experience.

---

## Analytics

Cloudflare Pages includes built-in Web Analytics free. No code to add. Look at the Cloudflare dashboard.

If you want more (search terms, retention, etc.), drop a Plausible Analytics or Fathom snippet into the HTML head (~$10/mo). Lighter and more privacy-friendly than Google Analytics.

---

## File structure

```
tantra-authority/
├── README.md                    (this site's strategic notes)
├── DEPLOY.md                    (this file)
├── index.html                   (homepage)
├── book.html                    (book funnel page)
├── about.html                   (about / imprint info)
├── styles.css                   (shared styles — clean, readable, calm)
├── articles/                    (every article = one HTML file here)
│   ├── what-tantra-actually-is.html
│   ├── tantric-breathing-truth.html
│   ├── (...add more...)
│   └── (eventually 30-200 articles)
├── assets/                      (images, etc. — empty for now)
└── _template/
    └── _layout.html             (template to copy for new articles)
```

Plain static HTML. No build step. No node_modules. No dependencies. Deploys in seconds.

---

## When the site grows past ~30 articles

At ~30 articles, consider:
- Adding a category structure (`articles/foundations/`, `articles/practice/`, `articles/relationships/`)
- Building a tiny script to regenerate `index.html` from a `articles/*.json` index (so you don't hand-maintain the homepage article list)
- Or: migrate to Astro / 11ty static site generator. Build step adds 30 seconds but lets you not touch HTML for new articles.

Not urgent. First 20 articles can be hand-maintained.
