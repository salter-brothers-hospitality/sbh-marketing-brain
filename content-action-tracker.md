# SBH Strategic Content Action Tracker

_Last updated: 11 August 2026_

**State:** In production 0/2 · In QA 0 · Live (awaiting measurement) 2 · Due for measurement: 20 Sep 2026

- **Status flow:** Candidate → Next up → Briefed → In Production → In QA → Live → Measured
- **WIP limit:** 2 actions in production at once
- **Measurement windows:** Organic Visibility 60 days · Conversion Performance 30 days · Brand & Editorial 60 days · Funnel Support 30 days (or end of campaign) · Structural n/a

Priority is simply the order of the table. The **Gate** column says whether an item can start: _Ready_, _Baseline needed_, _Technical track_ (runs in parallel, doesn't use the WIP limit), or _Blocked_.

## Actions

| ID | Action | Lever | Gate / track | Owner | Status | Live | Due | Notes |
|---|---|---|---|---|---|---|---|---|
| SCA-001 | Optimise /dine/high-tea-blue-mountains | Organic Visibility | Ready | Content Marketing Manager | Live | 22 Jul 2026 | 20 Sep 2026 | Live 22 Jul. Defence vs 57% decline (984 → 421). Primary "high tea blue mountains" pos 4 (vol 1,100). ⚠ At baseline the term's clicks were won by /independents/hydromajestic/dining/the-wintergarden, not this page (overlaps SCA-009) — confirm ownership was resolved at go-live, or the 20 Sep read is muddied. Secondary "hydro majestic high tea menu" held by the Hydro Majestic page. |
| SCA-002 | Optimise /stay/hunter-valley-accommodation | Organic Visibility | Ready | Senior Content Marketing Manager | Live | 22 Jul 2026 | 20 Sep 2026 | Live 22 Jul. Highest single-keyword upside in the portfolio. "hunter valley accommodation" vol 9,100, pos 10 → top 3. Baseline 29 Jun: 18,993 impressions / 0.11% page CTR — large impression base pinned below the click zone; clean attribution (3 URLs). Clusters with SCA-005. |
| SCA-003 | Audit and complete spicersretreats.com 301s | Organic Visibility | Technical track | Sanity dev / Tynan | Done | — | — | Complete (Jul–Aug). All 39 legacy URLs confirmed 301. Fixed 17 redirect chains (trailing-slash → no-slash canonical) and repointed spicers-hidden-peaks-cabins to its live page; remaining targets confirmed 200. Review legacy-session recovery at next monthly measurement. |
| SCA-004 | Diagnose /ardour/miltonpark decline | Organic Visibility | Ready | Tynan | Candidate | — | — | Diagnose before optimising. Down 10% with pos 1 holding → check GSC impressions vs CTR for a SERP-feature loss. Optimisation is a conditional follow-on. |
| SCA-005 | Optimise /weddings/hunter-valley-venues | Conversion Performance | Ready | Content Marketing Manager | Next up | — | — | "hunter valley wedding venues" vol 1,000, pos 7 → top 3. Brings the Conversion lever into reporting. Promoted to fill a slot freed by SCA-001/002 going live; clusters with the now-live SCA-002. |
| SCA-006 | Optimise /independents/lilianfels/wellness for "blue mountains spa" | Conversion Performance | Ready | Content Marketing Manager | Candidate | — | — | vol 600, pos 5 → top 3. |
| SCA-007 | Optimise Rick Stein at Bannisters page for "mollymook restaurants" | Organic Visibility | Ready | Content Marketing Manager | Next up | — | — | vol 500, pos 2 → 1. Low-effort win. Page: /bannisters/by-the-sea/dining/rick-stein. Promoted to fill the second freed slot. |
| SCA-008 | Build first 3 destination guides (/experiences/[region]) | Organic Visibility | Blocked: build | Senior Content Marketing Manager | Candidate | — | — | Minimum launch = 3 published together. Hunter Valley first to compound with SCA-002 and SCA-005. Gated on front-end template and Sanity schema. |
| SCA-009 | Brand-term saturation review (sub-page sprawl) | Structural | Blocked: dev | Tynan + Sanity dev | Candidate | — | — | Not a standard SCA, so no measurement window. Audit Tamarind, Hydro Majestic, Lilianfels and Hidden Vale for whether sub-pages should consolidate. Now also flagged by SCA-001 baseline: the high-tea query is split across the dine page, the Hydro Majestic property page and the Wintergarden dining page. |

## Baselines

Captured before optimisation so the pre/post comparison is clean. Pages flagged _Baseline needed_ above stay there until their baseline is logged here.

**Captured 29 June 2026** · window 4 May – 28 June 2026 (8 weeks) · sources: Ahrefs Site Explorer (AU) and Google Search Console via Ahrefs (project 9206176). GA4 organic sessions outstanding — to append.

**SCA-001 — /dine/high-tea-blue-mountains** (Organic Visibility, 60-day window)
- Primary "high tea blue mountains": Ahrefs position 4 (vol 1,100, KD 3); GSC query 125 clicks, 1,755 impressions, 7.12% CTR, avg position 7.75.
- Page totals (GSC): 965 clicks, 10,491 impressions, 9.20% CTR, avg position 7.55, 394 ranking queries.
- ⚠ Cannibalisation: GSC shows 21 URLs ranking for the term; clicks are won by /independents/hydromajestic/dining/the-wintergarden, not the target page. Resolve page ownership before briefing.
- GA4 organic sessions: _to append_.

**SCA-002 — /stay/hunter-valley-accommodation** (Organic Visibility, 60-day window)
- Primary "hunter valley accommodation": Ahrefs position 10 (vol 9,100, KD 37); GSC query 3 clicks, 2,421 impressions, 0.12% CTR, avg position 12.94 (clean — 3 URLs, target page on top).
- Page totals (GSC): 20 clicks, 18,993 impressions, 0.11% CTR, avg position 25.38, 916 ranking queries.
- Read: large impression base pinned just below the click zone; moving the head term from ~13 to top 3 is the lever.
- GA4 organic sessions: _to append_.

## How we keep this current

Tell me what changed — e.g. "SCA-001 briefed today, assigned to X" or "SCA-007 went live 2 July" — and I'll update the table, work out the Due date from the Live date plus the lever window, refresh the state line at the top, and add a dated entry to the log.

## Weekly standup

A standing ritual to keep the tracker current. There's no automated notification — set a recurring reminder (Outlook, Monday morning) and run this yourself. Paste the trigger into a chat with the marketing brain loaded, and I'll read the current state of this tracker and return a checklist of only what needs answering that week.

**Trigger:** `Weekly tracker standup`

**What I'll return**, derived from the live table above:

- **Production slots** — how many of the 2 WIP slots are open, and which Next up items are queued to fill them
- **Baselines outstanding** — any item gated _Baseline needed_ that can't start until its baseline is logged
- **Ready to promote** — Candidate items gated _Ready_ that could move to Next up
- **Blocked dependencies** — items gated _Blocked_ and what they're waiting on
- **Gone Live** — anything published since last week, so I can set its Due date from Live plus the lever window
- **Measurement due** — anything inside its measurement window or overdue, and the next monthly slot (last Friday)

Tell me what changed against any of these and I'll update the table, recompute Due dates, refresh the state line, and add a dated change-log entry.

## Change log

- **11 Aug 2026** — SCA-001 and SCA-002 went live 22 Jul; moved to Live, Due 20 Sep 2026 (Organic Visibility 60-day window). Both production slots freed.
- **11 Aug 2026** — SCA-003 redirect QA complete: 39 legacy 301s confirmed; fixed 17 chains and the hidden-peaks-cabins dilution redirect; remaining targets confirmed 200. Legacy-session recovery to review at next monthly measurement.
- **11 Aug 2026** — Promoted SCA-005 and SCA-007 to Next up to fill the two freed production slots.
- **29 Jun 2026** — Baseline captured for SCA-001 and SCA-002 (Ahrefs + GSC via project 9206176, window 4 May – 28 Jun). Both gates cleared from Baseline needed to Ready. GA4 organic sessions outstanding. SCA-001 cannibalisation flag added — page ownership to resolve before briefing; cross-referenced to SCA-009.
- **17 Jun 2026** — Adopted as the operational source of truth for content reporting, replacing the Google Sheet + Looker approach. Added the weekly standup section. See `content-reporting-framework.md`.
- **17 Jun 2026** — Tracker created with 9 actions from the May 2026 Ahrefs audit.
