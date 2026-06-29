# Skill: Content QA

## Purpose
Pre-publish quality assurance for content changes across worldsapart.club — journal pieces, SEO destination guides, property pages, and landing pages. The QA pass is the gate between a piece being drafted and being published. It catches voice violations, factual errors, broken links, and metadata gaps before they go live.

---

## Scope
Applies to all content changes, including:
- New journal articles publishing to `/journal/`
- New SEO destination guides under `/experiences/guides/`, `/dine/guides/`, etc.
- Updates and optimisation of existing property and landing pages (V1 work)
- Edits and amendments to live content

Not every section applies to every change. For minor edits (typo fixes, single link updates), run only the relevant sections. For new publishes and substantive updates, run all sections.

---

## 1. Voice

- [ ] Run the relevant skill's quality checklist first (`journal-skill.md`, `seo-content-skill.md`, `landing-page-skill.md`, `email-skill.md`, or `ad-copy-skill.md`)
- [ ] Australian spelling throughout
- [ ] No em dashes (Ardour content is the exception)
- [ ] No directive openers (Discover, Experience, Celebrate, Explore)
- [ ] No generic openers (Nestled, Situated, Set amidst, "Here —")
- [ ] No hyperbole (unrivalled, world-class, second to none)
- [ ] No comparative or correlative structures (Whether X or Y, From X to Y)
- [ ] No overused words (scrumptious, delectable, indulge, elevated, culinary journey, beauty)
- [ ] No prose ending with "Here..."
- [ ] Brand voice correctly applied to context (Worlds Apart for journal; respective sub-brand for property pages)
- [ ] Factual USPs over vague emotional claims

---

## 2. Accuracy

- [ ] Property names full and correct on first mention
- [ ] Rick Stein at Bannisters in full — never just "Rick Stein"
- [ ] Room counts, restaurant names, chef names, partner names match source of truth (brand `.md` files or the Sanity entry)
- [ ] Dates accurate (opening dates, stay dates, offer dates, blackout periods)
- [ ] Rates and inclusions match the latest offer documentation
- [ ] Sources verifiable for any factual claims (statistics, awards, quotes)
- [ ] Property locations and regions stated correctly

---

## 3. Links

- [ ] All internal links resolve — no 404s
- [ ] All external links function and open in a new tab where appropriate
- [ ] Anchor text reads meaningfully — never "click here" or "read more"
- [ ] Internal links point to current worldsapart.club URLs — no legacy spicersretreats.com URLs
- [ ] Where a `/experiences/[region]` destination guide exists for the region, the journal article links to it (reciprocal to the guide → journal rule)
- [ ] Property links go to the correct `/[brand]/[property]` URL
- [ ] UTM parameters applied to any outbound links from this page (e.g. CTA tracking)
- [ ] CTAs go to the right destination (booking engine, property page, related article, newsletter)

---

## 4. Metadata

- [ ] Meta title set, under 60 characters, reads as it should (editorial for journal, keyword-led for SEO pages)
- [ ] Meta description set, under 155 characters, benefit-led with a soft CTA
- [ ] OG image set (or hero image used as fallback)
- [ ] Canonical URL set — particularly important for any reposted or cross-published content
- [ ] Alt text on every image — descriptive, not "image1.jpg"
- [ ] Slug clean and readable in URL (no auto-generated strings)
- [ ] Publish date set correctly
- [ ] Taxonomy fields populated (brand, region, theme) for journal articles
- [ ] Schema markup applied where relevant (article, FAQ, breadcrumb)

---

## 5. Publishing and Technical

- [ ] Mobile preview checked across breakpoints
- [ ] Images optimised in Sanity (no bloated file sizes)
- [ ] Related content surfaces correctly — related Properties and Brands populated in Sanity for journal articles
- [ ] Featured flag set appropriately (journal articles only)
- [ ] Status moved from draft to published only after final sign-off
- [ ] GA4 tracking confirmed — page views fire correctly
- [ ] Change logged with approver name and date

---

## Sign-off

| Field | Detail |
|---|---|
| Page / piece |  |
| Content type | Journal article / SEO guide / Property page / Landing page / Other |
| Type of change | New publish / Substantive update / Minor edit |
| QA completed by |  |
| Date |  |
| Approved by |  |
| Status | Approved / Sent back for revision |

---

## Related Files
- `skills/journal-skill.md` — voice and structure for journal content
- `skills/seo-content-skill.md` — voice and structure for SEO destination guides
- `skills/landing-page-skill.md` — voice and structure for landing pages
- `skills/email-skill.md` — voice and structure for email
- `skills/ad-copy-skill.md` — voice and structure for ad copy
- `skills/content-action-brief-skill.md` — per-piece brief used pre-write
- `brands/brand-voice.md` — full cross-brand voice rules
