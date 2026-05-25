# Initial Ahrefs SEO Audit — worldsapart.club

**Date:** 25 May 2026
**Run by:** Tynan (Digital Marketing Manager)
**Country:** Australia
**Comparison window:** February 2026 vs May 2026

This is the baseline audit referenced in the content reporting framework. Findings are organised against the three Strategic Content Action priorities for V1 (Organic Visibility lever) work: declining pages to defend, cannibalisation to resolve, and keyword gaps to attack.

---

## Snapshot

### worldsapart.club (current platform)
- Organic keywords: 1,212
- Top 3 keywords: 597 (49% of total — strong position concentration)
- Organic traffic: 62,655
- Estimated traffic value: ~$13,931 AUD/month
- Domain Rating: in line with comparable Australian luxury hospitality domains

### spicersretreats.com (legacy)
- Organic keywords: 294
- Top 3 keywords: 133
- Organic traffic: 3,089

### Migration read
Worldsapart.club has successfully picked up the majority of organic equity — roughly 95% of the combined traffic now sits on the new domain. However, **188 keywords are common to both domains**, meaning the legacy site is still competing with worldsapart.club for shared terms. This is internal cannibalisation at the domain level and should be resolved by completing 301 redirects on any remaining live spicersretreats.com pages.

---

## Top Performing Pages

The top 10 pages drive ~62% of total organic traffic. Brand search dominates.

| Page | Traffic | Top Keyword | Position |
|---|---:|---|---:|
| /independents/hydromajestic | 9,726 | hydro majestic | 1 |
| /bannisters/by-the-sea | 5,677 | bannisters mollymook | 2 |
| /bannisters/port-stephens | 5,564 | bannisters port stephens | 1 |
| /independents/lilianfels | 5,163 | lilianfels | 1 |
| /spicers/hidden-vale | 2,553 | spicers hidden vale | 1 |
| /spicers/tamarind-retreat | 2,308 | spicers tamarind | 1 |
| /spicers/guesthouse | 1,989 | spicers hunter valley | 1 |
| /spicers/peak-lodge | 1,906 | spicers peak lodge | 1 |
| /spicers/sangoma-retreat | 1,659 | spicers sangoma retreat | 1 |
| /spicers | 1,624 | spicers retreat | 1 |

**Observation:** Brand search is doing its job. Non-brand traffic is the underdeveloped opportunity — and the V1 SEO lever is the place to attack it.

---

## Finding 1: Declining Pages

Three pages show real traffic decline over the comparison window (not migration-driven). These are the immediate defence priorities.

### Priority 1 — /dine/high-tea-blue-mountains
- **Traffic:** 984 → 421 (–57%)
- **Top keyword:** "hydro majestic high tea menu" (vol 400, pos 2)
- **Read:** This was a meaningful traffic page in Q1. Losing 563 monthly sessions on a guide page is the kind of decline that warrants immediate investigation. Likely causes: SERP feature changes, content freshness, ranking lost on a secondary keyword. Worth pulling GSC clicks-by-query history to confirm.
- **Action:** Strategic Content Action under Organic Visibility lever. Optimisation pass with focus on the "high tea blue mountains" keyword (vol 1,000, pos 5 currently — also a target).

### Priority 2 — /ardour/miltonpark
- **Traffic:** 1,403 → 1,265 (–10%)
- **Top keyword:** "milton park bowral" (vol 1,300, pos 1)
- **Read:** Flagship Ardour property page declining post-opening is unexpected. Position 1 holding but traffic dropping suggests either SERP feature loss (e.g. losing a featured snippet or knowledge panel position) or downstream keyword decay. Worth checking GSC for impressions vs CTR trend.
- **Action:** Strategic Content Action under Brand & Editorial or Organic Visibility lever. Diagnose before optimising — the cause matters here.

### Priority 3 — /independents/convent/dining/circa-1876
- **Traffic:** 617 → 569 (–8%)
- **Top keyword:** "circa 1876" (vol 1,000, pos 1)
- **Read:** Minor decline, low priority. Monitor.

---

## Finding 2: Cannibalisation

Cannibalisation appears at two levels: brand-term saturation (multiple worldsapart.club URLs in one SERP) and cross-property overlap.

### Pattern 1 — Brand term saturation

Several high-volume brand searches return 6+ worldsapart.club URLs in the top SERP. This isn't always harmful (sitelinks, image carousels, related pages can be legitimate), but it does signal that content architecture is sprawling and the property pages may be diluted by sub-pages competing for the brand term.

| Keyword | Volume | WA URLs in SERP |
|---|---:|---:|
| spicers tamarind | 1,800 | 10 |
| hydro majestic | 7,800 | 9 |
| lilianfels | 4,100 | 8 |
| spicers hidden vale | 3,900 | 8 |
| spicers retreat | 1,200 | 7 |
| spicers balfour | 1,000 | 7 |
| spicers clovelly | 1,100 | 7 |
| bannisters pavilion | 1,000 | 7 |

**Action:** Audit each of these properties for whether dining, experience, and wellness sub-pages are necessary as standalone URLs or could be consolidated. This is a structural decision, not a quick fix — flag for the content + Sanity dev conversation.

### Pattern 2 — Cross-property internal competition

Most cross-property cases resolve correctly (e.g. "spicers maleny" goes to Tamarind, "spicers grandchester" goes to Hidden Vale), but a few are worth checking:

| Keyword | Volume | Page ranking | Note |
|---|---:|---|---|
| spicers hunter valley | 1,400 | /spicers/guesthouse | Correct, but Vineyards Estate is also Hunter Valley |
| spicers retreat hunter valley | 350 | /spicers/vineyards-estate | Adjacent variant, different page |
| spicers blue mountains | 250 | /spicers/sangoma-retreat | Correct |
| spicers retreat blue mountains | 150 | /spicers/sangoma-retreat | Same URL, fine |
| bannisters port stephens | 4,900 | /bannisters/port-stephens (pos 1) + /bannisters/port-stephens/dining/rick-stein (pos 1) | Both at position 1 — likely SERP feature, but worth investigating |

**Action:** Light cleanup. The Hunter Valley split (Guesthouse vs Vineyards Estate) is the only one with material volume worth deciding on intentionally rather than letting Google sort.

### Pattern 3 — Legacy domain competition

188 keywords are shared between worldsapart.club and spicersretreats.com. The legacy domain still drives 3,089 monthly organic sessions. Without 301s, this equity will continue to bleed.

**Action:** Audit whether all spicersretreats.com URLs are 301'd. Any orphan URLs still serving content need redirecting. Strategic Content Action under Organic Visibility lever — likely a one-off technical pass, not ongoing content work.

---

## Finding 3: Keyword Gaps and Opportunities

The most actionable finding from the audit. These are existing pages already ranking but not at top 3 — V1 optimisation candidates with measurable upside.

### Major opportunity — Hunter Valley accommodation

**"hunter valley accommodation"** is currently ranking at position 10 on /stay/hunter-valley-accommodation with a search volume of **5,900**. Moving this page to top 3 would add an estimated 1,500-2,500 monthly organic sessions on a high-intent commercial keyword.

This is the single highest-value V1 action visible in the audit. Worth its own brief and a focused optimisation pass.

### Mid-tier optimisation candidates

| Keyword | Volume | Current Page | Current Pos | Target |
|---|---:|---|---:|---|
| hunter valley accommodation | 5,900 | /stay/hunter-valley-accommodation | 10 | Top 3 |
| high tea blue mountains | 1,000 | /dine/high-tea-blue-mountains | 5 | Top 3 |
| hunter valley wedding venues | 1,000 | /weddings/hunter-valley-venues | 7 | Top 3 |
| blue mountains spa | 600 | /independents/lilianfels/wellness | 5 | Top 3 |
| mollymook restaurants | 500 | /bannisters/by-the-sea/dining/rick-stein | 2 | Position 1 |

Combined, these five keywords represent ~9,000 in monthly search volume. Even partial improvement across the set is material.

### Destination DMO competitors to attack

The competitive landscape shows three categories:
1. **OTAs/aggregators** (TripAdvisor, Booking.com, Luxury Escapes) — not competable on volume, defend brand search
2. **Destination Marketing Organisations** (visitnsw.com, visitbluemountains.com.au, winecountry.com.au, portstephens.org.au) — *this is the content opportunity*
3. **Direct hotel competitors** (fairmontresort.com.au punching above its weight in Blue Mountains)

The DMOs own destination-led queries that worldsapart.club is well-positioned to compete on: regional accommodation guides, "things to do in [region]," seasonal travel content, wedding and event venue queries. These are natural SEO destination guide candidates (live under /experiences/guides/, /dine/guides/, etc., per the content reporting framework — not under /journal/).

---

## Recommended Strategic Content Actions

Pulled directly from the audit. Each warrants a Content Action Brief.

### High Priority — Defence and high-value optimisation
1. **Investigate and optimise /dine/high-tea-blue-mountains** — defence against 57% traffic decline. Lever: Organic Visibility.
2. **Diagnose /ardour/miltonpark decline** — root cause before optimising. Lever: Organic Visibility.
3. **Optimise /stay/hunter-valley-accommodation** — biggest single-keyword upside in the portfolio. Lever: Organic Visibility.
4. **Audit and complete spicersretreats.com 301s** — stop the equity leak. Lever: Organic Visibility (technical).

### Medium Priority — Mid-tier optimisation
5. **Optimise /dine/high-tea-blue-mountains for "high tea blue mountains"** — bundle with action 1.
6. **Optimise /weddings/hunter-valley-venues** — position 7 → top 3 target. Lever: Conversion Performance (commercial intent).
7. **Optimise /independents/lilianfels/wellness for "blue mountains spa"** — position 5 → top 3. Lever: Conversion Performance.
8. **Optimise /bannisters/by-the-sea/dining/rick-stein for "mollymook restaurants"** — position 2 → position 1. Lever: Organic Visibility.

### Structural — Not standard SCAs, separate workstream
9. **Brand-term saturation review** — Audit top brand pages (Spicers Tamarind, Hydro Majestic, Lilianfels, Hidden Vale) for sub-page sprawl. Decide whether dining/wellness/experience sub-pages should be consolidated or kept. Coordinate with Sanity dev.

### Long-tail — New content opportunity (V1 SEO destination guides)
10. **Build destination guide content under /experiences/guides/ targeting DMO-held queries** — regional accommodation, things to do, wedding venues, seasonal guides. Each guide is its own Strategic Content Action.

---

## Out of Scope (For This Audit)
- Detailed competitor backlink analysis
- Page-level technical SEO audit (Core Web Vitals, schema, crawl issues)
- Property-level keyword opportunity mapping (one property at a time)
- New journal content topic research
- Paid search overlap analysis

These can be scoped as separate audits once V1 priorities are in flight.

---

## Next Steps
1. Convert the High Priority recommendations into Content Action Briefs (`skills/content-action-brief-skill.md`)
2. Assign owners and target publish dates
3. Schedule the first Monthly Measurement Slot (last Friday of June 2026) — these baselines become the pre-measurement reference
4. Capture parallel GSC baselines for each affected page before optimisation begins (task 1 dependency)
