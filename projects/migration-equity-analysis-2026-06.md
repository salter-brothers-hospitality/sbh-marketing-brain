# worldsapart.club Migration Equity Analysis

_June 2026. Source: chat baseline pull, 15 June 2026._

**Method:** Ahrefs Site Explorer, AU, organic. Domain-level pulls use `subdomains` mode with the bare domain; property-section pulls use `prefix` mode with the full URL including protocol and `www` (e.g. `https://www.worldsapart.club/independents/lilianfels`). Legacy baseline date **15 June 2025** — the last point all nine legacy domains were live and standalone. Consolidated date **15 June 2026**. A 1 April 2026 snapshot was tested as a pre-migration baseline and rejected: only the late-wave domains (Spicers, Bannisters) still showed live traffic, while the earlier-wave Independents already read at or near zero, making that date a contaminated baseline. Traffic value shown as Ahrefs' A$/mo estimate.

**Migration waves:**
- **Late wave — 14 April 2026:** spicersretreats.com, bannisters.com.au
- **Earlier wave:** the Independent properties and Ardour-pipeline sites (hydromajestic.com.au, lilianfels.com.au, miltonpark.com.au, kingsfordbarossa.com.au, parklands.com.au, convent.com.au, echoeshotel.com.au)

---

## 1. Consolidated baseline — worldsapart.club, 15 June 2026

| Metric | Value |
|---|---|
| Organic traffic | 76,331 /mo |
| Organic keywords | 1,780 |
| Keywords in top 3 | 807 |
| Organic traffic value | ~A$17,610 /mo |
| Paid traffic / keywords / pages | 7,615 / 204 / 133 |

worldsapart.club had zero indexed organic presence at 15 June 2025, so the consolidated side is a 0-to-now build.

---

## 2. Cumulative (before) vs consolidated (now)

| Metric | Legacy cumulative (Jun 25) | worldsapart.club (Jun 26) | Change |
|---|---:|---:|---:|
| Organic traffic | 103,773 | 76,331 | −26.4% |
| Keywords in top 3 | 1,273 | 807 | −36.6% |
| Traffic value (A$/mo) | ~25,771 | ~17,610 | −31.7% |
| Live domains | 9 | 1 | consolidated |

Consolidated domain currently holds **~74%** of the pre-migration organic footprint.

---

## 3. Property-level equity recovery

Each legacy domain vs its current worldsapart.club section (full prefix, all sub-pages counted), sorted by gap size.

| Property | Wave | Legacy (Jun 25) | Current section (Jun 26) | Recovery | Gap |
|---|---|---:|---:|---:|---:|
| Spicers (all) | 14 Apr (late) | 35,947 | 26,191 | 73% | −9,756 |
| Bannisters (all) | 14 Apr (late) | 24,979 | 18,761 | 75% | −6,218 |
| Lilianfels | Earlier | 13,220 | 7,455 | 56% | −5,765 |
| Hydro Majestic | Earlier | 16,638 | 11,999 | 72% | −4,639 |
| The Convent | Earlier | 3,031 | 1,474 | 49% | −1,557 |
| Milton Park* | Earlier | 3,519 | 1,993 | 57%* | −1,526 |
| Echoes | Earlier | 2,214 | 1,611 | 73% | −603 |
| Parklands | Earlier | 1,515 | 1,210 | 80% | −305 |
| Kingsford The Barossa | Earlier | 2,710 | 2,414 | 89% | −296 |
| **Sections total** | | **103,773** | **73,108** | **70%** | **−30,665** |

Property sections total 73,108; the remaining ~3,223 of the domain's 76,331 is net-new platform/guide content (`/stay/`, `/dine/` guides, homepage) with no single legacy-property owner.

\* Milton Park was closed for restoration in June 2025, so its legacy 3,519 was brand/zombie traffic against a shut property. Treat its current 1,993 as a fresh post-reopening baseline, not a recovery shortfall.

---

## 4. Read

The −26% splits into two stories.

**~16,000 of the gap is "young".** Spicers and Bannisters only migrated 14 April, sit at 73–75% at nine weeks, and are driving the domain's +22% climb over the three weeks to 15 June. Expect most of this to close by the 90-day mark (mid-July). Action: monitor, don't intervene; re-baseline at the 90-day point before calling any permanent loss.

**~12,000 is "stale".** The early-wave Independents have had their full recovery window and still land at only 66% cumulatively. It concentrates in three names:

- **Lilianfels — 56%, −5,765.** Worst result in the portfolio in both percentage and near-largest in absolute terms. The old domain carried heavy wellness/spa and dining (Darley's) content that hasn't reappeared at strength. A redirect-and-content problem, not a recovery-lag one. Some branded-demand decline here is demand-side rather than migration damage.
- **Hydro Majestic — 72%, −4,639.** Better rate, but it's the single biggest organic page in the portfolio; 4,600 missing sessions is material. Early wave, so the gap is stale.
- **The Convent — 49%, −1,557.** Worst percentage on the board. The Circa 1876 restaurant page survived the move; the main property page didn't carry its equity across.

These three need a redirect audit and content rebuild — they are the ones to brief.

---

## 5. Lilianfels lost-keyword diagnosis

Comparing the old lilianfels.com.au ranking set against what `/independents/lilianfels` holds now, the primary culprit is the **`/spa` → `/wellness` page migration**. A non-branded spa/wellness keyword cluster — including "blue mountains spa," "day spa blue mountains," "blue mountains sauna" — dropped from position 2 to position 5–6, or fell out of the index entirely. That cluster accounts for roughly **1,200 of Lilianfels' 5,765-session gap**. The audit had already flagged the wellness page as a top-3 target.

---

## Recommended next actions

1. **Lilianfels** — run the redirect audit on `/spa` → `/wellness`; rebuild the wellness/spa content cluster and Darley's dining content to reclaim the non-branded spa terms.
2. **Hydro Majestic** — run the same lost-keyword diagnosis; it's the single biggest organic page, so even a partial recovery is material.
3. **The Convent** — diagnose why the main property page didn't carry equity across; the Circa 1876 page survived, the property page didn't.
4. **Spicers / Bannisters** — monitor only; re-baseline at the 90-day mark (mid-July) before treating any of the ~16,000 young gap as permanent loss.

---

## Related files
- `projects/ahrefs-audit-2026-05.md` — the initial audit; flags the Lilianfels wellness page as a top-3 target
- `content-reporting-framework.md` — the reporting framework these findings feed into as Organic Visibility actions
- `content-action-tracker.md` — where any resulting Strategic Content Actions are tracked
