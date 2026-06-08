# Project: Destination Guide Build — /experiences/[region]

## Overview
Implementation-ready scope for SEO-driven destination guides on worldsapart.club at `/experiences/[region]`. These pages target informational keywords ("things to do [region]") and serve as top-of-funnel regional discovery pages that convert to SBH property interest. They are distinct from accommodation pages (no keyword cannibalisation) and from journal articles (structured templates, not editorial pieces).

---

## Decisions Locked
- URL pattern: `/experiences/[region]` (e.g. `/experiences/hunter-valley`, `/experiences/blue-mountains`)
- Primary keyword target: `things to do [region]` — informational intent, not transactional
- No cannibalisation with accommodation or booking pages — separate keyword sets
- Page template is fixed and structured (not a free-form editorial layout)
- SBH property booking CTAs are embedded within the page — guests do not need to leave the guide to check availability
- Content voice follows the relevant SBH brand present in the region; Worlds Apart platform voice for multi-brand or brand-agnostic regions
- Content production briefs follow `skills/destination-guide-skill.md`

---

## In Scope
- URL structure and slug convention for `/experiences/[region]`
- One reusable front-end page template
- Sanity document type: Destination Guide
- Anchor navigation component (links to page sections)
- Region Snapshot block (stat cards)
- Experiences by Category section (tabbed or sectioned card layout)
- Insider Picks section (vertical card or numbered list)
- Where to Stay section (property cards with booking CTA)
- Practical Guide section (seasonal info, getting around, local tips)
- FAQ section with accordion behaviour (for featured snippet eligibility)
- Getting Here section (travel options table or card grid)
- SEO meta fields per page (title tag, meta description, canonical, OG image)
- Internal linking to property pages and relevant journal articles
- Schema markup: TouristDestination and/or LocalBusiness
- Mobile-responsive layout across all breakpoints

---

## Out of Scope
- Journal articles at `/journal/` — separate scope and template (see `projects/worldsapart-journal-build-scope.md`)
- Campaign landing pages — governed by `skills/landing-page-skill.md`
- Accommodation and booking pages — existing scope, separate keyword targets
- User-generated content, reviews, or ratings
- Map embed (can be added in a future iteration)
- Filtering or sorting within the Experiences section (future iteration if needed)
- Automated content generation — all copy is human-produced per brief

---

## URL Structure
- `/experiences/` — index page (optional: directory of all destination guides)
- `/experiences/[region-slug]` — individual destination guide pages
- Slug format: lowercase, hyphenated region name — e.g. `hunter-valley`, `blue-mountains`, `barossa-valley`

---

## Template Structure

The page is structured in eight sections, in this order:

1. **Hero** — full-width image, H1 (region name), one-sentence descriptor, anchor nav
2. **Region Snapshot** — stat card block (distance, travel time, best season, what it's known for, SBH properties present)
3. **Getting Here** — short prose intro + travel options table/cards (drive, fly, train/coach where applicable)
4. **Experiences by Category** — tabbed or sectioned experience cards, filterable by category
5. **Insider Picks** — curated concierge-style recommendations, vertical layout
6. **Where to Stay** — SBH property cards with embedded booking CTAs
7. **Practical Guide** — scannable sub-sections: When to Go, What to Pack, Getting Around, Local Tips
8. **FAQ** — accordion, 4–6 questions per page targeting long-tail keywords

Full copy and content specifications for each section are in `skills/destination-guide-skill.md`.

---

## Sanity Schema

New document type: **Destination Guide**

| Field | Type | Notes |
|---|---|---|
| title | string | Region name only (e.g. "Hunter Valley") — required |
| slug | slug | Generated from title, required. Format: lowercase, hyphenated |
| descriptor | string | One-sentence region description — required |
| heroImage | image | Required, with alt text |
| regionSnapshot | object | Key stats: drive times, fly times, bestSeason, knownFor, goodFor |
| gettingHere | object | Prose intro + structured travel options (array: from, driveTime, flyTime, trainTime) |
| experienceCategories | array of objects | Each: categoryName (enum), cards (array: image, name, description, ctaLabel, ctaUrl, externalUrl) |
| insiderPicks | array of objects | Each: venueName, whatItIs, whyItsBest, practicalNote (optional) |
| whereToStay | array of references | References to existing Property documents in Sanity |
| practicalGuide | object | Sub-sections: whenToGo, whatToPack, gettingAround, localTips |
| faq | array of objects | Each: question (string), answer (Portable Text) |
| relatedProperties | array of references | References to existing Property documents — drives internal linking |
| relatedBrands | array of references | References to existing Brand documents |
| taxonomyRegion | string | e.g. "Hunter Valley", "Blue Mountains" |
| taxonomyState | enum | NSW, QLD, SA, VIC |
| primaryKeyword | string | e.g. "things to do hunter valley" — internal reference only |
| seoTitleTag | string | ≤60 chars — required |
| seoMetaDescription | string | ≤155 chars — required |
| seoCanonicalUrl | url | Optional — self-referencing canonical |
| seoOgImage | image | Optional — falls back to heroImage |
| status | enum | draft, published, archived |

**Experience category enum values:**
`food-and-wine`, `nature-and-outdoors`, `arts-and-culture`, `wellness`, `adventure`, `family`

---

## Component Inventory

| Component | Type | Notes |
|---|---|---|
| Hero (full-width + anchor nav) | New | Region-specific variant — not the same as accommodation hero |
| Region Snapshot block | New | Stat card grid — 4–6 cards |
| Getting Here table/cards | New | Drive/fly/train rows, multiple origin cities |
| Experience category tabs | New | Tab or scroll-spy nav switching between category sections |
| Experience card | New or extend existing | Image + name + 2–3 sentence desc + optional CTA |
| Insider Pick card | New | Vertical layout — name, one-liner, hook, practical note |
| Property card (Where to Stay) | Extend existing | Use or adapt existing property card component; add "Check availability" CTA |
| Practical Guide section | New | Sub-sections with scannable formatting |
| FAQ accordion | New or extend existing | Standard accordion; schema markup for featured snippets |

---

## SEO Requirements
- Schema markup: `TouristDestination` and/or `LocalBusiness` per page
- FAQ schema: `FAQPage` schema applied to the FAQ section for featured snippet eligibility
- Internal links: every destination guide must link to at least one SBH property page and, where available, one relevant journal article
- Sitemap: all published destination guides included
- Canonical: self-referencing on all pages

---

## Dependencies
- Sanity CMS schema configuration
- Front-end development resource
- Design resource for page template and all new components
- Image library (Sanity asset pipeline) — hero and experience card images required per page
- Existing Property documents in Sanity (Where to Stay section references these)
- Content production: one brief per region, following `skills/destination-guide-skill.md`
- Minimum viable launch: 3 destination guides published simultaneously

---

## Priority Regions (Proposed Launch Order)

| Region | SBH Properties | State |
|---|---|---|
| Hunter Valley | Spicers Vineyards Estate | NSW |
| Blue Mountains | Lilianfels (Ardour pipeline) | NSW |
| Barossa Valley | Kingsford The Barossa (Ardour pipeline) | SA |
| Kangaroo Valley | Spicers Sangoma Retreat | NSW |
| Sunshine Coast Hinterland | Spicers Clovelly Estate, Spicers Tamarind Retreat | QLD |

---

## Stakeholders
- Digital Marketing Manager (Tynan) — project owner
- Senior Content Marketing Manager / Content Marketing Manager — content production
- Sanity developer — schema and CMS configuration
- Front-end developer — template and component build
- Designer — template design, component design
- Group Director of Marketing Performance — approver

---

## Open Questions
1. **Index page at `/experiences/`.** Does this exist as a hub page listing all destination guides, or do destination guides only exist as individual pages? A hub page adds build scope but improves crawlability and internal linking.
2. **Booking engine integration.** Does "Check availability" in the Where to Stay section deep-link directly to the booking engine with property pre-selected, or go to the property page? Direct to booking engine is higher-converting but requires a confirmed URL pattern from the dev/PMS team.
3. **Experience card external links.** Linking out to third-party operators and venues (e.g. cellar doors, activity providers) is good for UX and E-E-A-T, but needs a policy decision: do all external links open in new tab? Are there any categories of venue we don't link to?
4. **Image sourcing for experiences.** Property images exist in Sanity. Experience card images for non-SBH venues (wineries, national parks, etc.) need sourcing — confirm whether this is licensed stock, commissioned photography, or third-party embeds.
5. **Insider Picks authorship.** Are picks attributed to "the concierge team at [property]", to Worlds Apart editorially, or left unattributed? Attribution strengthens E-E-A-T but needs to be consistent.
6. **Getting Around — car hire partnerships.** Is there an affiliate or referral opportunity here with a car hire provider? If yes, needs separate commercial sign-off before adding to the template.

---

## Acceptance Criteria
- `/experiences/[region]` pages render correctly for all published destination guides
- All eight template sections render and are populated from Sanity
- Anchor navigation scrolls to the correct section on click
- Experience category tabs/sections function correctly on desktop and mobile
- FAQ accordion opens and closes correctly; FAQPage schema is valid (test via Google Rich Results)
- Where to Stay property cards link correctly to property pages and/or booking engine
- SEO meta (title, description, OG) surfaces correctly in page source and social share previews
- Internal links to property pages are present and correct
- Mobile responsive across all breakpoints
- Page load performance meets existing worldsapart.club benchmarks
- GA4 tracking confirmed: page views, scroll depth, anchor nav clicks, CTA clicks (Where to Stay)

---

## Related Files
- `skills/destination-guide-skill.md` — content production brief, page structure, copy rules, quality checklist
- `skills/seo-content-skill.md` — SEO copy rules and process
- `projects/worldsapart-journal-build-scope.md` — adjacent build scope (journal)
- `brands/brand-voice.md` — per-brand copy rules
- `projects/ahrefs-audit-2026-05.md` — SEO audit context and keyword opportunity data
