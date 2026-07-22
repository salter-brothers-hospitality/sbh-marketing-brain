# Skill: Schema (JSON-LD)

## Purpose
Producing schema.org JSON-LD for worldsapart.club pages so every output shares one entity graph, one host convention, and one set of type mappings. Call this whenever a page needs structured data — property pages, `/stay/` accommodation pages, `/experiences/` destination guides, `/journal/` articles, and offer/dining/wellness/events pages. The goal is alignment: two people (or two Claude sessions) building schema for different pages should produce nodes that stitch into the same graph rather than fragment it.

Schema describes what is already on the page. It never invents facts, and it is not a substitute for on-page content.

---

## Global Conventions (every build)

- **Host:** `https://www.worldsapart.club` — always `www`, always `https`.
- **Trailing slash:** root only (`https://www.worldsapart.club/`). No trailing slash on deep paths (`/ardour/lilianfels`, not `/ardour/lilianfels/`). This matches the live canonical and OG tags.
- **URL currency:** every `url` and `@id` uses the current worldsapart.club URL. Legacy domains (`lilianfels.com.au`, `spicersretreats.com`, brand microsites) never appear as `url` or `@id` — they are only ever permitted inside `sameAs`.
- **Language:** `inLanguage: en-AU`. Australian spelling in all text fields.
- **Voice:** `name`, `description`, and `caption` fields follow the copy non-negotiables in `brands/brand-voice.md` and CLAUDE.md — no "indulgent/indulgence", "luxurious", "iconic"; no directive or generic openers; no hyperbole. The Ardour em-dash exception applies only to Ardour property descriptions.
- **Source of truth:** pull `name`, address, phone, email, the property list (and its order), on-page FAQ text, and the canonical URL from the **live page** at build time — not from memory. Names change at rebrand; property lists change per page.

---

## Shared Nodes (identical on every page)

Every page's `@graph` opens with these three nodes, byte-for-byte identical. This is what consolidates the graph — if the `@id`s or host drift between pages, Google sees duplicate WebSite/Organization entities.

```json
{
  "@type": "WebSite",
  "@id": "https://www.worldsapart.club/#website",
  "url": "https://www.worldsapart.club/",
  "name": "Worlds Apart",
  "alternateName": ["Worlds Apart Club", "worldsapart.club"],
  "publisher": { "@id": "https://www.worldsapart.club/#organization" },
  "inLanguage": "en-AU"
},
{
  "@type": "Organization",
  "@id": "https://www.worldsapart.club/#organization",
  "name": "Worlds Apart",
  "alternateName": ["Worlds Apart Club"],
  "url": "https://www.worldsapart.club/"
},
{
  "@type": "Brand",
  "@id": "https://www.worldsapart.club/#brand",
  "name": "Worlds Apart",
  "alternateName": "Worlds Apart Club",
  "url": "https://www.worldsapart.club/"
}
```

---

## `@id` Fragment Convention

Build every node `@id` as `[page-url]#fragment`, using the canonical no-trailing-slash URL:

| Fragment | Node |
|---|---|
| `#webpage` | The page node (WebPage, CollectionPage, etc.) |
| `#hotel` | The Hotel / LodgingBusiness |
| `#breadcrumb` | BreadcrumbList |
| `#primaryimage` | Primary ImageObject |
| `#properties` | ItemList of properties |
| `#faq` | FAQPage |

Cross-page references use the **target page's own** `#hotel` `@id`. When a `/stay/` ItemList lists Spicers Vineyards Estate, it references `https://www.worldsapart.club/spicers/vineyards-estate#hotel` — the same `@id` that property's own page emits — so the hotel is one entity across the site, not one per page it appears on.

---

## Page Type → Schema Map

| Page type | URL pattern | Primary type | Supporting nodes | Notes |
|---|---|---|---|---|
| Property / hotel | `/[brand]/[property]` | `Hotel` | WebPage `#webpage`, BreadcrumbList, ImageObject `#primaryimage` | Full NAP. Rebrands: see below. |
| Accommodation category ("stay") | `/stay/[region]-accommodation` | `CollectionPage` | ItemList `#properties`, BreadcrumbList, `about` → Place, FAQPage `#faq` if a FAQ is on the page | **Transactional. Never use `TouristDestination` here** — that belongs on `/experiences/`. |
| Destination guide | `/experiences/[region]` | `TouristDestination` (optionally + `LocalBusiness`) | BreadcrumbList, FAQPage `#faq` | Informational counterpart to the `/stay/` page. Distinct primary type prevents cannibalisation. |
| Journal / blog | `/journal/[slug]` | `Article` (or `BlogPosting`) | `author` → Organization `#organization`, `publisher` → `#organization`, `image`, BreadcrumbList | |
| Offer | `/[brand]/[property]/offers/[slug]` | `Offer` within the property `Hotel` | WebPage | Reference the parent `#hotel`; don't restate full NAP. |
| Dining / Wellness | `/[brand]/[property]/dining|wellness/...` | `Restaurant` / `HealthAndBeautyBusiness` | WebPage, reference parent `#hotel` | Lightweight. |

The four page types above the line are defined in full below; the rest are extensions of the same pattern.

---

## Node Requirements

### Hotel / LodgingBusiness
- **Required:** `name` (current marketing name), `url`, `address` (full `PostalAddress`), `telephone` (`+61 …` format), `image[]`.
- **Recommended:** `email`, `amenityFeature[]`, `checkinTime`, `checkoutTime`, `brand` → `#brand`, `sameAs[]`.
- **Rebrands (e.g. Independents → Ardour):** `name` = current name; `alternateName` = the prior and short-form names for entity continuity (`["Ardour Lilianfels", "Lilianfels Blue Mountains Resort & Spa", "Lilianfels"]`); keep third-party `sameAs` (TripAdvisor, Booking, Expedia); verify or drop the property's own legacy domain if it now redirects.

### CollectionPage + ItemList
- **CollectionPage:** `name` (keyword-led, matches the H1), `description` (the page's meta description), `isPartOf` → `#website`, `about` → `Place` (the region), `breadcrumb`, `mainEntity` → the ItemList.
- **ItemList:** `numberOfItems` and `itemListElement` in the **same order the properties appear on the page**. Each item is a `Hotel` with its own `#hotel` `@id`, `name`, `url`, and `address`. Mirror the page — if the page shows four properties, the list has four.

### FAQPage
- Only when a FAQ is **visibly present** on the page.
- `Question` names and `Answer` text must match the on-page wording **verbatim** — Google requires the structured data to match visible content. Do not paraphrase, add questions, or reorder.

### BreadcrumbList
- Reflects site IA; every `item` is a real, resolvable URL.
- Convention: crumb 1 is **"Stay" → `/stay`**. Then — property pages: `[Collection]` (`/[brand]`) → `[Property]`; category pages: `[Page]`.

---

## Process

1. Identify the page type and look it up in the map.
2. Fetch the live page (and each property page it references): canonical URL, NAP, property list and order, on-page FAQ.
3. Assemble the `@graph`: shared nodes → page node → supporting nodes.
4. Apply the host, trailing-slash, and `@id` conventions.
5. Apply the copy non-negotiables to every text field.
6. Validate (below). Resolve warnings before shipping.

---

## Validation Checklist

- [ ] Valid JSON; single `@graph`; one `<script type="application/ld+json">` per page
- [ ] Shared WebSite / Organization / Brand nodes present and identical to the block above
- [ ] Host is `https://www.worldsapart.club`; no trailing slash on deep paths; no legacy domains outside `sameAs`
- [ ] Every `@id` follows `[page-url]#fragment`; cross-references resolve within the graph
- [ ] Hotel nodes carry full NAP sourced from the live page
- [ ] ItemList order mirrors the on-page property order; each property `@id` matches its own page
- [ ] FAQ text matches the page verbatim
- [ ] Breadcrumb items resolve and follow the Stay → `/stay` convention
- [ ] Text fields pass the brand non-negotiables and Australian spelling
- [ ] Passes the Google Rich Results Test and the schema.org validator

---

## Examples

**Property (Hotel).** Ardour Lilianfels Blue Mountains — `Hotel` (full NAP, `alternateName` carrying the pre-rebrand names) + `WebPage` + `BreadcrumbList` (Stay → Ardour → property) + primary `ImageObject`. Single `@graph` opening with the three shared nodes.

**Accommodation category (CollectionPage).** `/stay/hunter-valley-accommodation` — `CollectionPage` (`about` → Place "Hunter Valley") + `ItemList` of the four on-page properties in page order, each referencing its own `#hotel` `@id` + `BreadcrumbList` (Stay → page) + `FAQPage` mirroring the 12 on-page questions.

```
@graph:
  WebSite (#website)         ← shared
  Organization (#organization) ← shared
  Brand (#brand)             ← shared
  CollectionPage (#webpage)  → about: Place, mainEntity: #properties
  ItemList (#properties)     → 4 × ListItem → Hotel (#hotel per property)
  BreadcrumbList (#breadcrumb)
  FAQPage (#faq)             → verbatim on-page Q&A
```

---

## Related Files
- `brands/brand-voice.md` — copy non-negotiables applied to schema text fields
- `skills/seo-content-skill.md` — meta title / description for the same pages
- `skills/destination-guide-skill.md` — `/experiences/` pages (`TouristDestination` + `FAQPage`)
- `skills/content-qa-skill.md` — internal-link resolution and URL-currency checks at QA
- `projects/destination-guide-build-scope.md` — schema requirements for guides
