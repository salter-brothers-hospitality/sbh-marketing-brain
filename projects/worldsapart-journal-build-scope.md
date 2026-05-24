# Project: Worlds Apart Journal Build

## Overview
Implementation-ready scope for the build of the worldsapart.club editorial journal at `/journal/`. Strategic decisions are locked; this document specifies what gets built, what doesn't, and what the development and design teams need to action.

---

## Decisions Locked
- `/journal/` sits at the top level of worldsapart.club
- The section is editorial only — SEO-driven destination guides are housed under topical parents (`/experiences/guides/`, `/dine/guides/`, etc.) and governed by `skills/seo-content-skill.md`
- No filtered views per brand at URL level — one curated journal destination
- No filter UI on the index page — taxonomy is metadata only
- Voice is Worlds Apart platform voice throughout, governed by `skills/journal-skill.md`
- Per-piece briefs follow `skills/content-action-brief-skill.md`

---

## In Scope
- URL structure for `/journal/` index and articles
- Two front-end templates: index page and article template
- One new Sanity document type: Journal Article
- Reference fields linking journal articles to existing Property and Brand documents
- Taxonomy as metadata for related-content surfacing and analytics segmentation
- SEO meta fields per article (title tag, meta description, canonical, OG image)
- Standard social share functionality
- Newsletter signup module embedded in article template

---

## Out of Scope
- SEO destination guides under `/experiences/guides/`, `/dine/guides/`, etc. — separate scope
- Migration of legacy editorial content from spicersretreats.com or elsewhere
- Article comment functionality
- Author profile pages or Author Sanity document type (see Open Questions)
- Editorial calendar or publishing workflow tooling
- Custom analytics dashboard — use existing GA4 / Looker Studio
- Filter UI on the journal index

---

## URL Structure
- `/journal/` — section index, lists published articles in reverse chronological order
- `/journal/[slug]` — individual article URLs, slug generated from article title

---

## Templates Required

### 1. Journal Index Page
- Featured article module (one hero piece at top, manually flagged in Sanity)
- Article grid: hero image, headline, dek, publish date
- Pagination or infinite scroll
- Newsletter signup module
- Consistent with the existing worldsapart.club design system

### 2. Journal Article Template
- Hero image and headline
- Byline (if confirmed — see Open Questions) and publish date
- Article body (prose, H2, H3, blockquote, in-line images, links)
- Related content module — three articles surfaced via taxonomy match
- Property / brand reference module — surfaces relevant property pages when an article features specific properties
- Soft editorial CTA (e.g. "See availability at [property]")
- Social share functionality
- Newsletter signup module
- SEO meta handled in CMS

---

## Sanity Schema

New document type: **Journal Article**

| Field | Type | Notes |
|---|---|---|
| title | string | required |
| slug | slug | generated from title, required |
| dek | string | optional, used in cards and meta description fallback |
| heroImage | image | required, with alt text |
| body | Portable Text | supports H2, H3, blockquote, image, links |
| publishedAt | datetime | required |
| updatedAt | datetime | auto |
| author | string or reference | format depends on Open Question 3 |
| relatedProperties | array of references | references to existing Property documents |
| relatedBrands | array of references | references to existing Brand documents |
| taxonomyBrand | enum | Worlds Apart, Spicers, Ardour, Bannisters, Independents |
| taxonomyRegion | enum | QLD, NSW, SA, etc. |
| taxonomyTheme | enum | Stay, Dine, Wellness, Experiences, Events |
| seoTitleTag | string | ≤60 chars |
| seoMetaDescription | string | ≤155 chars |
| seoCanonicalUrl | url | optional |
| seoOgImage | image | optional, falls back to heroImage |
| isFeatured | boolean | controls hero placement on index |
| status | enum | draft, published, archived |

---

## Taxonomy Approach
- Pure metadata — never appears in URLs, never used for index filtering UI
- Drives related-content surfacing logic (taxonomy match selects related articles)
- Supports GA4 content segmentation
- Allows future flexibility without committing to URL or UI structure now

---

## Dependencies
- Sanity CMS schema configuration
- Front-end development resource
- Design resource for index and article templates
- Image library access (Sanity asset pipeline)
- Confirmed content runway before launch (see Open Questions)

---

## Stakeholders
- Digital Marketing Manager (Tynan) — project owner
- Senior Content Marketing Manager and Content Marketing Manager — editorial production
- Sanity developer — schema and CMS configuration
- Front-end developer — template build
- Designer — template design
- Group Director of Marketing Performance — approver

---

## Open Questions
1. **Publishing cadence at launch.** Monthly is the floor for the section to feel alive. Fortnightly is the ideal. Needs sign-off from the content team before build begins.
2. **Content runway.** Three to five pieces ready at launch is the recommendation, so the index doesn't read as sparse.
3. **Author bylines.** Are articles bylined? If yes, is the byline a plain string or does it reference a proper Author document type (with profile pages)? Author doc type adds build scope.
4. **Newsletter integration.** The existing Worlds Apart signup is Jotform-based — confirm whether the journal uses the same form or has its own integration.
5. **Image specs.** Hero image aspect ratio and minimum dimensions need confirming with design.
6. **Soft CTA logic.** Manual per article, or auto-pulled from `relatedProperties`? Manual gives editorial control; auto is lower-friction.

---

## Acceptance Criteria
- `/journal/` index page renders and lists all published Journal Articles in reverse chronological order
- `/journal/[slug]` article URLs render correctly for all published articles
- Sanity Journal Article document type configured with all specified fields
- Front-end templates pass design and accessibility QA
- SEO meta surfaces correctly in page source and social shares
- Internal links from articles to property and brand pages function correctly
- Related content module surfaces relevant pieces via taxonomy match
- Mobile responsive across all breakpoints
- Page load performance meets existing worldsapart.club benchmarks
- GA4 tracking confirmed (page views, scroll depth, internal click-throughs)

---

## Related Files
- `skills/journal-skill.md` — voice, structure, and non-negotiables for journal content
- `skills/content-action-brief-skill.md` — per-piece content brief template
- `brands/brand-worlds-apart.md` — platform brand context
- `brands/brand-voice.md` — cross-brand voice rules
