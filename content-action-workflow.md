# Content Action Workflow

## Purpose
Defines how a Strategic Content Action is executed end to end — the specific tools, skills, inputs, and outputs at each stage of the pipeline. It is the *how-to* layer that sits between three documents that already exist:

- `content-reporting-framework.md` owns the **definitions and the measurement rules** — what counts as an action, the four levers, the measurement windows, the monthly slot, and force-close. This workflow does not restate those; it references them.
- The **skill files** (`seo-content-skill.md`, `destination-guide-skill.md`, `journal-skill.md`, `landing-page-skill.md`, `omnichannel-copy-skill.md`) own **how to write** each format and which voice applies.
- `content-action-tracker.md` is the **live state** — every stage transition below is recorded there.

This workflow is the connective tissue: it says which tool measures the baseline, which skill drafts the piece, which gate vets it, and where it gets built — and it keeps each handoff aligned with the stack in `about-me.md` and `channel-strategy.md`.

---

## Where this sits

```
content-reporting-framework.md   →   what counts, which lever, when to measure
        │
content-action-workflow.md        →   how to execute: measure · draft · vet · create   (this file)
        │
skills/*-skill.md                 →   how to write each format, which voice
        │
content-action-tracker.md         →   the live state of every action
```

---

## The execution spine

Every action moves through the same spine. The four verbs map onto the pipeline stages defined in the framework.

| Stage (tracker status) | Verb | Primary tools | Governing skill / doc | Owner | Tracker action |
|---|---|---|---|---|---|
| Candidate → Next up | — | Ahrefs, the source audit | `content-reporting-framework.md` | Tynan | Set lever, gate, order |
| Baseline-needed gate | **Measure** | Ahrefs · GSC · GA4 (by lever) | this file → Tooling by Lever | Tynan | Log figures in Baselines; gate → Ready |
| → Briefed | — | Claude (claude.ai) | `content-action-brief-skill.md` | Tynan / owner | Status → Briefed; assign owner + date |
| → In Production | **Draft** | Claude · Surfer SEO · Ahrefs/GSC term data | the format skill + `brand-voice.md` | CMM / Senior CMM | Status → In Production (WIP ≤ 2) |
| → In QA | **Vet** | `content-qa-skill.md` · Surfer score · Sanity cross-check | `content-qa-skill.md` | Owner + reviewer | Status → In QA |
| → Live | **Create** | Sanity (CMS) · Claude Code (brain files) | the relevant build scope | Sanity dev / owner | Set Live date; compute Due; status → Live |
| → Measured | **Measure** | Ahrefs · GSC · GA4 (same as baseline) | `content-reporting-framework.md` | Tynan | Log outcome in Notes; status → Measured |

WIP limit of two applies to In Production only. Technical-track items (e.g. SCA-003 redirects) run in parallel and do not consume a slot.

---

## Stage by stage

### 0. Intake and triage (Candidate → Next up)
- **Source:** actions originate from an audit (`projects/ahrefs-audit-2026-05.md`) or a diagnosed decline. Each must fit one of the four levers, or it is not a Strategic Content Action.
- **Assign:** lever, owner, and a gate — Ready, Baseline needed, Technical track, or Blocked.
- **Output:** a row in the tracker in priority order. No tools beyond Ahrefs and the audit at this stage.

### 1. Baseline capture — MEASURE (the Baseline-needed gate)
The pre-optimisation snapshot, captured before any change so the pre/post comparison is clean. Tools depend on the lever (full mapping in Tooling by Lever below). The constant: **pull a clean, equal-length pre window** (e.g. the last 8 weeks) so it is directly comparable to the post window.

- **Organic Visibility:** Ahrefs (target keyword volume + best position, page `sum_traffic`), GSC (page clicks, impressions, CTR, average position for the target queries), GA4 (page-level organic sessions).
- **Conversion Performance:** GA4 (page-level conversion rate, booking-engine click-through events); plus Ahrefs/GSC for the keyword where there is a ranking component.
- **Brand & Editorial:** GA4 (sessions, average engagement time, internal click-through), plus the current email subscriber count where the journal feeds it.
- **Output:** figures logged in the tracker's **Baselines** section, dated. Gate flips from _Baseline needed_ to _Ready_.

### 2. Brief (→ Briefed)
- **Skill:** `content-action-brief-skill.md` for journal and most pieces; the Content Production Brief template inside `destination-guide-skill.md` for guides.
- **Approval:** brief approved and owner assigned per the framework's "Briefed" definition.
- **Output:** completed brief; tracker status → Briefed with owner and target publish date.

### 3. Draft — DRAFT (→ In Production)
Route to the format skill; the skill sets structure and voice, `brand-voice.md` sets the non-negotiables, applied line by line — not at review.

| Content type | Skill | Voice | Surfer SEO? |
|---|---|---|---|
| Property / SEO landing / category page | `seo-content-skill.md` | Sub-brand (or Worlds Apart for multi-brand hubs) | Yes |
| Destination guide `/experiences/[region]` | `destination-guide-skill.md` | Brand present in region; WA if multi-brand | Yes |
| Journal `/journal/` | `journal-skill.md` | **Worlds Apart, always** | No — editorial, not ranking-led |
| Offer / campaign landing page | `landing-page-skill.md` | Sub-brand | Optional |
| Multi-channel campaign copy | `omnichannel-copy-skill.md` | Per channel matrix | Per channel |

- **Tools:** Claude (claude.ai) as the drafting aid against the skill; Surfer SEO for term coverage on SEO and guide content; Ahrefs/GSC to confirm the target term set before drafting.
- **Output:** draft copy, tracker status → In Production (respect WIP ≤ 2).

### 4. Vet — VET (→ In QA)
`content-qa-skill.md` is the gate between drafted and published. Nothing publishes without it.

- Run the format skill's own checklist first, then the QA pass: **voice** (non-negotiables, correct brand voice for context), **accuracy** (property names, room counts, partners checked against the brand `.md` files and the Sanity entry — Rick Stein at Bannisters always in full), **links** (resolve, no legacy `spicersretreats.com` URLs, UTM on outbound CTAs), **metadata** (title ≤60, description ≤155, schema, alt text, slug).
- **Tools:** Surfer SEO score checked against target for SEO/guide pieces; Sanity entry cross-check for facts; link check.
- **Output:** QA sign-off recorded; tracker status → In QA, then cleared for Live.

### 5. Create and publish — CREATE (→ Live)
- **Existing page (most V1 optimisations):** edit in place in Sanity. Update body, SEO meta fields, internal links, and schema markup. No new template needed.
- **Net-new page type (destination guides, journal):** built against the build scope — `projects/destination-guide-build-scope.md` or `projects/worldsapart-journal-build-scope.md` — with the Sanity schema, front-end template, and design dependencies those scopes specify. This is where the Sanity dev and front-end resource are required.
- **Two commit paths, kept distinct:** page content is published in **Sanity**; any change to a brain file (a skill, this workflow, the tracker) is committed via **Claude Code**. Don't conflate them.
- **Internal linking:** apply the linking rules in the relevant skill and build scope, including the journal → `/experiences/[region]` rule where a guide exists for the region.
- **Output:** published page; tracker status → Live with the **Live date** set, and **Due** computed as Live date + the lever window.

### 6. Measure outcome — MEASURE (→ Measured)
At the lever window, re-pull the **same tools used at baseline** and compare.

- This is a batch task, run in the monthly measurement slot (last Friday), not per-piece.
- Log the pre/post delta against the lever's outcome metric in the tracker **Notes**; status → Measured.
- Apply the framework's force-close rule for anything Live and overdue by 60+ days with no documented reason.

---

## Tooling by lever

The outcome metric — and therefore the tool you measure with at both baseline and outcome — is set by the lever. Windows are owned by the framework and repeated here only for line-of-sight.

| Lever | Window | Baseline + outcome tools | Metric measured |
|---|---|---|---|
| Organic Visibility | 60 days | **Ahrefs** (keyword position), **GSC** (impressions, CTR, indexed pages), **GA4** (page-level organic sessions) | Position movement, organic sessions, CTR |
| Conversion Performance | 30 days | **GA4** (conversion rate, booking-engine click-through), booking data | Page conversion rate, bookings/value attributed |
| Brand & Editorial | 60 days | **GA4** (sessions, engagement time, internal CTR), **Revinate/ADM** (subscriber growth) | Engagement, time on page, journal → property CTR |
| Funnel Support | 30 days / campaign end | Campaign reporting + **Looker Studio**, **Revinate** (email), paid platform / GA4 | Campaign contribution, email + paid engagement |

Supporting tools across all levers: **BigQuery** for custom queries where GA4's interface is insufficient; **Looker Studio** for the monthly volume and quarterly outcome reports, generated from the tracker.

---

## Worked example — SCA-002, Optimise /stay/hunter-valley-accommodation

Organic Visibility · 60-day window · the portfolio's highest single-keyword upside. A full walk of the spine.

1. **Measure (baseline).** Ahrefs: "hunter valley accommodation" volume 5,900, best position 10, plus the page's `sum_traffic` and secondary keyword set. GSC: page clicks, impressions, CTR, average position for that query over a clean 8-week pre window. GA4: organic sessions to the page over the same window. Log all in the Baselines section; gate → Ready.
2. **Brief.** Own brief (the audit flagged it as warranting one), `content-action-brief-skill.md`, owner Senior CMM, intent commercial, primary keyword plus the secondary cluster, internal-link targets named (Spicers Guesthouse, Spicers Vineyards Estate, The Convent).
3. **Draft.** `seo-content-skill.md`, destination/accommodation-page intent. Surfer SEO for term coverage. Voice confirmed in the brief — Worlds Apart for the multi-property hub. Non-negotiables applied line by line.
4. **Vet.** `content-qa-skill.md`: Surfer score to target, internal links to the three property pages resolve, no legacy URLs, meta title ≤60 and description ≤155, schema present.
5. **Create.** Existing page — edit in place in Sanity. Update body, meta, internal links, schema; publish. Set Live date; Due = Live + 60 days; status → Live.
6. **Measure (outcome).** At 60 days, re-pull Ahrefs position (target top 3), GSC clicks/CTR, GA4 sessions. Log the delta in Notes; status → Measured at the monthly slot.

**How a Conversion action differs (e.g. SCA-006, blue mountains spa):** the spine is identical, but the lever shifts the measure verb. Baseline and outcome are pulled in **GA4** — page conversion rate and booking-engine click-through — over a **30-day** window, with Ahrefs position as a secondary read rather than the headline metric.

---

## Related files
- `content-reporting-framework.md` — definitions, levers, measurement windows, monthly slot, force-close
- `content-action-tracker.md` — the live state this workflow transitions
- `skills/content-action-brief-skill.md` — the brief at the Briefed stage
- `skills/content-qa-skill.md` — the gate at the Vet stage
- `skills/seo-content-skill.md`, `destination-guide-skill.md`, `journal-skill.md`, `landing-page-skill.md`, `omnichannel-copy-skill.md` — format and voice at the Draft stage
- `projects/destination-guide-build-scope.md`, `projects/worldsapart-journal-build-scope.md` — build dependencies at the Create stage
- `campaign-workflow.md` — the parallel workflow for campaigns
- `about-me.md`, `channel-strategy.md` — the stack these tools sit in
