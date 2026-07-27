# Skill: Structured Data (Schema)

## Purpose
Defining and generating JSON-LD structured data for every page on worldsapart.club. This skill is the single source of truth for which schema types and required fields apply to each Sanity `pageType`, so any Claude instance can generate correct, valid schema for a given page.

Scope is **manual authoring** for now — schema is written per page against this reference, then handed to the dev (Nightjar) to inject. Sanity-templated auto-generation (a schema component that reads document fields and emits JSON-LD dynamically) is a later phase and is not covered here. See the note under Process.

**How to invoke:** paste a worldsapart.club page URL. From that URL alone, this skill detects the page's Sanity `pageType`, reads the visible content, and produces the correct JSON-LD `@graph` for that page. See Process for the exact flow (and the one fetch caveat to watch for).

---

## Output Format
- One `<script type="application/ld+json">` block per page.
- A single `@graph` array holding every node for that page. Do not output multiple disconnected script blocks.
- Nodes are linked by `@id`, not duplicated. The `@id` is the page URL plus a fragment (e.g. `https://www.worldsapart.club/experiences/hunter-valley#collectionpage`).
- Every page shares two base nodes for the platform — `WebSite` and `Organization` (see Base Nodes) — referenced by `@id` rather than repeated in full.
- Injected **server-side** into the rendered HTML, not via Google Tag Manager. GTM fires on the deferred second-wave render and is less reliable for crawlers. (Confirmed against the live Hunter Valley page — the DOM is server-rendered, so schema belongs in the SSR output.)
- Self-referencing `canonical` must be present on the page (this is a page requirement, not part of the JSON-LD, but is checked here).

---

## Base Nodes (every page)
These two nodes appear in the `@graph` on every page and are referenced by `@id` from the page-level node:

- `WebSite` — `@id` `…/#website`. name "Worlds Apart", url, publisher → the Organization.
- `Organization` — `@id` `…/#organization`. name "Worlds Apart", url, logo. This is the platform-level entity that individual brand and hotel nodes link up to via `parentOrganization`.

---

## Process

**Input: a single worldsapart.club URL.** Paste the page URL and the schema is produced from it — no other input required. The steps below are what to run against that URL.

1. **Fetch the page.** Retrieve the URL.
2. **Confirm a full render.** Check the response contains the Sanity `__NEXT_DATA__` payload and the deeper page sections (FAQs, where-to-stay, etc.). ⚠️ **Known issue on this site:** the fetch tool sometimes returns a truncated pre-hydration cache that silently drops lower sections. The live page is server-rendered, so Googlebot sees everything — but a partial fetch will make the schema incomplete. If the fetch looks truncated (no `__NEXT_DATA__`, or missing sections you'd expect), **ask for the full page source to be pasted in** and work from that. This is how the Hunter Valley guide was built correctly.
3. **Detect the pageType.** Read `pageType` from `__NEXT_DATA__` (authoritative). Use the URL pattern below as a fast first guess and a sanity check:

   | URL pattern | Likely pageType | Notes |
   |---|---|---|
   | `/` | `page` (home) | base nodes + hub ItemList |
   | `/experiences/[region]` | `page` (destination guide) | e.g. `/experiences/hunter-valley` |
   | `/[brand]` (e.g. `/spicers`, `/ardour`, `/bannisters`, `/independents`) | `hotelGroup` | brand hub |
   | `/[brand]/[property]` (e.g. `/spicers/guesthouse`, `/independents/convent`) | `hotel` | property page |
   | room / suite pages under a property | `accommodation` | confirm via `__NEXT_DATA__` — path varies |
   | experience / activity pages | `experience` | confirm via `__NEXT_DATA__` — path varies |
   | restaurant pages | `dining` | confirm via `__NEXT_DATA__` — path varies |
   | `/offers/[slug]` | `page` (offer) | |
   | `/journal/[slug]` | `page` (journal article) | |
   | `/weddings`, `/meetings`, `/celebrations` | `page` (events) | |

   The URL is only a hint — `pageType` in the payload wins whenever they disagree.
4. **For `page`, identify the functional variant** (home/hub, destination guide, offer, journal article, weddings/meetings/celebrations) — these share a pageType but take different schema.
5. **Look up** the required and recommended schema in Page Types and Schema below.
6. **Populate every field from visible on-page content** — pull names, descriptions, geo, address, telephone, breadcrumb, FAQ, and list items from the rendered page / payload. Never from assumption or from data that isn't shown to the user.
7. **Apply the Global Rules** and honour the three defaults in Decisions to Confirm.
8. **Output** one `<script type="application/ld+json">` block with a single `@graph`.
9. **Validate** in Google Rich Results Test **and** the Schema.org validator before handing to dev. Both must pass clean.

> **Later phase (not in scope):** the end state is a Sanity-driven schema component built by Nightjar that reads existing document fields (location, tags, excerpt, featuredImages, parent, geo) and emits this JSON-LD automatically, removing per-page hand-authoring. When that's scoped it becomes `projects/schema-build-scope.md`. Until then, author manually against this skill.

---

## Global Rules
- **Match visible content.** Every value in the schema must correspond to something shown on the page. Schema that describes content the user can't see is a structured-data violation.
- **FAQ answers verbatim.** `Question`/`acceptedAnswer` text must match the on-page FAQ word for word.
- **Never fabricate reviews or ratings.** Do not add `aggregateRating` or `review` unless first-party reviews are genuinely displayed on the page. Do not republish third-party ratings (Google, TripAdvisor) as first-party `aggregateRating` — this is a penalty risk. See Decisions to Confirm.
- **No invented prices.** Rates are dynamic (Duetto / SiteMinder). Do not hard-code a price that isn't shown. See Decisions to Confirm.
- **Australian spelling** in all human-readable string values (descriptions, names), consistent with the copy non-negotiables. Schema keywords themselves are fixed schema.org vocabulary and are not "spelling".
- **One entity per real-world thing.** A hotel is one `Hotel` node reused by `@id`; don't mint a second node for the same property on the same page.
- **Canonical host.** Every emitted `url` and `@id` uses `https://www.worldsapart.club` — always `www`, always `https`. This is the live canonical; brand or legacy domains never appear as a `url` or `@id`.
- **Self-referencing `@id`s** using the page's canonical URL plus a fragment.

---

## Page Types and Schema
Organised by Sanity `pageType`, cross-referenced to the intent buckets in `seo-content-skill.md` (Transient/Accommodation, Package/Offer, Destination/Category, Meetings and Events).

### `hotel` — property page
*Intent bucket: Transient / Accommodation*
- **Primary:** `Hotel` (a subtype of `LodgingBusiness`).
- **Required fields:** name, url, image, description, address (`PostalAddress`), geo (`GeoCoordinates`), telephone, `containedInPlace` (the region/locality), `brand` → the parent `hotelGroup` Organization, `parentOrganization` → Worlds Apart.
- **Recommended:** `priceRange` (loose, `$$`–`$$$$`), amenityFeature, checkinTime/checkoutTime, `hasMap`.
- **Supporting nodes:** `BreadcrumbList`.
- ⚠️ **`aggregateRating`: omit by default** — no first-party on-page review module is currently visible. See Decisions to Confirm.

### `accommodation` — room / suite page
*Intent bucket: Transient / Accommodation*
- **Primary:** `HotelRoom` (or `Accommodation`), linked to its parent property via `containedInPlace` → the `Hotel` node's `@id`.
- **Required fields:** name, description, image.
- **Recommended:** `bed` (`BedDetails`), `occupancy` (`QuantitativeValue`), `amenityFeature`, `floorSize`.
- **Supporting nodes:** `BreadcrumbList`.
- ⚠️ **Price / `Offer`: omit hard price by default** (dynamic rates). Include an `Offer` only if a "from" price is actually displayed. See Decisions to Confirm.

### `experience` — bookable activity page
*Intent bucket: Destination / Category (activity)*
- **Primary (default):** `TouristAttraction`, with `isPartOf` / `provider` → the hotel that runs it.
- **Required fields:** name, description, image, `touristType` where relevant.
- **Supporting nodes:** `BreadcrumbList`.
- ⚠️ **Modelling choice:** default `TouristAttraction` (evergreen, enquiry-based — not dated `Event`s). Upgrade path is `Product` + `Offer` if/when price and online booking are exposed. See Decisions to Confirm.

### `dining` — restaurant page
*Intent bucket: Transient / Accommodation (F&B) — high rich-result value*
- **Primary:** `Restaurant`.
- **Required fields:** name, url, image, `servesCuisine`, address, geo, telephone, `containedInPlace` → the `Hotel` node, `priceRange`, `acceptsReservations`.
- **Recommended:** `hasMenu` (menu url), `openingHoursSpecification`.
- **Supporting nodes:** `BreadcrumbList`.
- Genuinely rich-result-eligible (restaurant results), so worth doing well. Examples: Circa 1876, Rick Stein at Bannisters.
- ⚠️ **`aggregateRating`: omit** unless first-party reviews are displayed. See Decisions to Confirm.

### `hotelGroup` — brand hub page (Ardour, Bannisters, Independents, Spicers)
*Intent bucket: Destination / Category (brand)*
- **Primary:** `CollectionPage`, with the brand modelled as an `Organization` (`parentOrganization` → Worlds Apart).
- **Structure:** `CollectionPage` → `mainEntity` → `ItemList` of member `Hotel` nodes (by `@id`).
- **Supporting nodes:** `BreadcrumbList`, the base `Organization` for the brand.

### `page` → destination guide (e.g. Hunter Valley) ✅ worked reference
*Intent bucket: Destination / Category*
- **Primary:** `CollectionPage` as the root.
- **Structure:** `about` → `TouristDestination` (geo, `containedInPlace` state, `touristType`, `containsPlace` → the member hotels); `mainEntity` → `ItemList` (things to do); `hasPart` → `FAQPage`; `breadcrumb` → `BreadcrumbList`.
- **LocalBusiness is deliberately excluded** — it belongs on property pages, not the region guide. (This supersedes the old one-liner in `destination-guide-skill.md`, which recommended LocalBusiness/TouristDestination and is now wrong.)
- Full worked example: `hunter-valley-schema.json`.

### `page` → home / section hub (Stay, Dine, Wellness, Experiences)
- **Primary:** `CollectionPage` (or `WebPage` for the home page), plus the base `WebSite` + `Organization` nodes.
- **Structure:** `mainEntity` → `ItemList` of the child pages/properties where the hub lists them.
- **Supporting nodes:** `BreadcrumbList`.

### `page` → offer / package page
*Intent bucket: Package / Offer*
- **Primary:** `CollectionPage` (or `WebPage`).
- ⚠️ **`Offer` / `AggregateOffer`: include only if concrete** — a real, stated offer with terms/validity. Otherwise omit. See Decisions to Confirm.
- **Supporting nodes:** `BreadcrumbList`.

### `page` → journal article ⚠️ blocked
*Intent bucket: Destination / Category (editorial)*
- **Primary:** `Article` / `BlogPosting`, with `author`, `publisher` → Organization, `datePublished`, `image`, `headline`.
- **Supporting nodes:** `BreadcrumbList`; `FAQPage` if the article carries an FAQ.
- ⚠️ **Blocked on the journal author byline decision** (worldsapart-journal-build-scope, Open Question 3: plain-string author vs an `Author` reference document type). `author` modelling can't be finalised until that lands. Everything else in the article node can be drafted now.

### `page` → weddings / meetings / celebrations
*Intent bucket: Meetings and Events*
- **Primary (default):** `WebPage`, or `Service` (`serviceType`) where the page sells a defined service.
- **Recommended:** event venues can carry `EventVenue` / `Place` with capacity where the page states specific room capacities.
- **Supporting nodes:** `BreadcrumbList`.

### `errorPage` — 404
- No schema. Nothing to mark up.

---

## Decisions to Confirm
These three set the defaults above. Current default is stated; flip any and I'll update the mapping.

1. **Reviews / `aggregateRating`** — *Default: OMIT everywhere.* No first-party on-page review module is currently visible. If a legitimate, on-page review source is added (e.g. a Revinate or TripAdvisor display that actually shows reviews on the page), `aggregateRating` on `hotel` and `dining` becomes the single biggest rich-result / CTR lever. Never mark up third-party ratings as first-party.
2. **Pricing** — *Default: omit hard prices; loose `priceRange` (`$`–`$$$$`) on restaurants only.* Rates are dynamic via Duetto / SiteMinder, so hard-coded prices in schema go stale and risk mismatch penalties.
3. **Experiences modelling** — *Default: `TouristAttraction`.* Evergreen and enquiry-based rather than scheduled `Event`s. Move to `Product` + `Offer` only if price and online booking get exposed on experience pages.

---

## Examples

### Good — Hunter Valley destination guide (worked reference)
Single `@graph`, seven linked nodes: `WebSite`, `Organization`, `CollectionPage` (root), `TouristDestination` (geo -32.78 / 151.30, `containedInPlace` NSW, `containsPlace` = the three properties), `BreadcrumbList` (Home › Experiences › Hunter Valley), `ItemList` (things to do, ordered), `FAQPage` (answers verbatim). LocalBusiness excluded. Full file: `hunter-valley-schema.json`.

### Bad — common mistakes to avoid
- `LocalBusiness` on a destination guide (it's a region, not a business).
- `aggregateRating` populated from Google's star rating when no reviews are shown on the page.
- A hard `price` on a room page pulled from a rate that changes daily.
- FAQ `acceptedAnswer` text paraphrased instead of matching the on-page copy.
- Schema injected via GTM, arriving after the first-wave render.
- Multiple separate `<script type="application/ld+json">` blocks instead of one `@graph`.

---

## Quality Checklist

**Structure**
- [ ] One `<script type="application/ld+json">` block, one `@graph`
- [ ] Base `WebSite` + `Organization` nodes present and referenced by `@id`
- [ ] All `@id`s self-referencing (page URL + fragment); nodes linked, not duplicated
- [ ] Correct primary schema type for the Sanity `pageType`
- [ ] `BreadcrumbList` present (all page types except 404)

**Accuracy**
- [ ] Every value maps to visible on-page content
- [ ] FAQ answers verbatim
- [ ] No fabricated `aggregateRating` / `review`
- [ ] No hard-coded dynamic prices
- [ ] `parentOrganization` / `brand` chain correct (hotel → brand → Worlds Apart)
- [ ] Australian spelling in human-readable string values

**Ship**
- [ ] Passes Google Rich Results Test
- [ ] Passes Schema.org validator
- [ ] Injected server-side, not via GTM
- [ ] Self-referencing canonical present on the page

---

## Related Files
- `hunter-valley-schema.json` — worked reference example (destination guide)
- `skills/destination-guide-skill.md` — the schema one-liner there (LocalBusiness/TouristDestination) is superseded by this skill; that line should point here
- `skills/content-qa-skill.md` — the "Schema markup applied where relevant" checklist item should reference this skill
- `skills/seo-content-skill.md` — page-type intent buckets cross-referenced above
- `projects/worldsapart-journal-build-scope.md` — journal author byline decision blocks the article `author` modelling
- `projects/schema-build-scope.md` — *(later phase, not yet created)* Sanity-driven auto-generation spec
