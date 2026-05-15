# Tantra Authority

The first vertical site in the 100-fishing-lines portfolio. Built 2026-05-14 (Japan) as the per-vertical template prototype.

**Live target:** `tantraauthority.com` (owned by Lawrence, Cloudflare DNS)
**Backup domain:** `tantra-authority.com` (redirect → primary)
**Deploy via:** Cloudflare Pages (see `DEPLOY.md`)

---

## What this site is

Tantra Authority is the **practical, SEO-friendly, educational** front door to Lawrence Gregory's tantra body of work. It is NOT the personal Substack. It is the authoritative, depersonalized destination for people who type "what is tantra" or "tantric breathing exercises" into Google.

**Persona:** The Tantra Authority Editors. Bylineless in most cases. Calm, authoritative, anti-bullshit, body-grounded.

**NOT this voice:**
- Not the punk-philosophical Naked Mind voice
- Not Lawrence speaking in first-person about his own life (most articles)
- Not edgy / Tantra Rebel voice
- Not certificate-program upsells / weekend-workshop sales
- Not Sanskrit-heavy / mystically-decorated

**IS this voice:**
- Educational. Patient. Confident.
- Stripped of mythology while honoring the practices
- Physiologically grounded ("here's what's actually happening in your body")
- Anti-cult / anti-guru (explicitly)
- Generally written in third person about the field
- Funnels to *Beyond the Myth: The Definitive Guide to Modern Tantra* + The Naked Mind newsletter

## Funnel architecture

```
Google search → Tantra Authority article →
  email signup (Substack form) →
  drip into The Naked Mind →
  preorder Beyond the Myth: Definitive Guide to Modern Tantra
```

Every article ends with the same CTA card pointing to the book. Inline newsletter signup on homepage and article pages.

## Content strategy

**Target: 30 articles in first 90 days.** Mix of:
- Foundations articles (what tantra is, the five primitives, brief history)
- Practice articles (specific techniques readers can do tonight)
- Reframe articles (what tantra is NOT — why most tantric content fails)
- Couples articles (partner practices, communication, conflict + tantra)
- Anti-cult articles (the dark side of the tantra teacher industry — high search interest)

After 30 articles, the long tail of SEO traffic should be enough that the site self-sustains traffic. Then we focus on:
- Featured articles (longer-form, ranking for high-volume queries)
- Book preorder conversion
- Email list growth

## Seeded articles (built 2026-05-14)

- `articles/what-tantra-actually-is.html` — foundational, ~2200 words
- `articles/tantric-breathing-truth.html` — practical, ~1500 words

Both end with the standard CTA + book funnel.

## Open / pending

- [ ] Connect newsletter forms to Substack (or ConvertKit / Buttondown — see DEPLOY.md)
- [ ] Add the remaining 3 articles previewed on the homepage:
  - `articles/why-most-tantric-sex-doesnt-work.html`
  - `articles/five-body-technologies.html`
  - `articles/tantric-practices-for-couples.html`
- [ ] Deploy to Cloudflare Pages (see DEPLOY.md)
- [ ] Set up custom domain (tantraauthority.com)
- [ ] Set up redirect from tantra-authority.com
- [ ] Add Cloudflare Web Analytics
- [ ] Replicate template structure for next vertical (suggest: open-relationship-blueprint)

## Notes

Built as plain static HTML (no build step) for maximum speed-to-ship and zero dependency hell. When article count exceeds ~30 or content needs more structure (categories, tags, search), consider migrating to Astro or 11ty. Not urgent.
