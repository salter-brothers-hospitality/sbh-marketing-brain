# Content Reporting Framework

## Purpose
Defines what qualifies as a **Strategic Content Action** and how the content function is reported to leadership in its MVP state. Designed to give marketing leadership visibility into content output and outcomes without over-engineering the reporting layer.

This framework governs reporting only. It does not replace campaign-level reporting (see `campaign-workflow.md`) or channel-level reporting (see `channel-strategy.md`). The tool-level mechanics of executing an action are governed by `content-action-workflow.md`, and the live state of every action lives in `content-action-tracker.md`.

---

## What is a Strategic Content Action

A **Strategic Content Action** is any piece of content work that:

1. Has been briefed using the Content Action Brief template (`skills/content-action-brief-skill.md`)
2. Has a defined business outcome it is intended to support (organic visibility, conversion, brand engagement, or funnel support)
3. Has an identified owner and target publish date

The definitional anchor is simple: **if it warrants a Content Action Brief, it is a Strategic Content Action and is counted in reporting. If not, it isn't.**

This rule is deliberate. It means ad-hoc, reactive, or single-paragraph requests do not crowd the reporting layer, and it gives the content function a defensible position when triaging stakeholder requests. Anyone who wants their request counted as content output needs to put it through a brief.

---

## What Does Not Count

The following are not Strategic Content Actions and are not reported under this framework:

- Typo fixes and minor copy corrections
- One-off ad-hoc copy requests not tied to a defined outcome (these are BAU service work)
- Property-led copy edits made without a central brief
- Reactive copy supporting a campaign already owned and reported elsewhere (the campaign owns the metric)
- Metadata-only updates outside of a broader optimisation effort
- Internal documentation updates
- Email subject line tweaks or send-time experiments (owned by email/CRM reporting)

If a piece of work falls into this list and is causing recurring volume, that is a signal to formalise it into a Strategic Content Action — not to start counting it without one.

---

## Lever Categories

Every Strategic Content Action is assigned to one of four levers. The lever determines what outcome metric the action is reported against.

### 1. Organic Visibility
Actions intended to drive organic search performance — new SEO destination guides, optimisation of existing property and landing pages, content restructures targeting specific keyword clusters.

**Reported against:**
- Organic sessions (page-level)
- Keyword position changes (tracked in Ahrefs)
- Indexed pages and click-through rate (tracked in GSC)

### 2. Conversion Performance
Actions intended to lift the conversion rate of a specific page or flow — landing page restructures, package page optimisation, CTA refinements, content additions to high-intent pages.

**Reported against:**
- Page-level conversion rate (GA4)
- Bookings or booking value attributed to the page
- Click-through to booking engine

### 3. Brand and Editorial
Actions intended to build brand affinity, engagement, and editorial presence — journal articles, longform features, feature placements that warrant a brief.

**Reported against:**
- Sessions and engagement (GA4)
- Average time on page
- Internal click-through rate (journal → property / category pages)
- Email subscriber growth attributed to the journal

### 4. Funnel Support
Actions that produce content assets supporting paid, email, or CRM funnels — landing pages for campaigns, email content (where it warrants a brief beyond standard offer comms), supporting content for paid amplification.

**Reported against:**
- Campaign performance contribution (where attributable)
- Email engagement (open/click rate of supported sends)
- Paid campaign metrics where content was a defined input

---

## Pipeline Stages

Every Strategic Content Action moves through five stages. Stage tracking is the core volume metric in MVP reporting.

| Stage | Definition |
|---|---|
| **Briefed** | Content Action Brief filled, approved, and assigned |
| **In production** | Drafting in progress |
| **In QA** | Drafted and submitted for QA against `content-qa-skill.md` |
| **Live** | Published or page change deployed |
| **Measured** | Pre/post comparison completed against the lever's outcome metric. Window varies by lever — see Measurement Schedule and Enforcement below |

The "Measured" stage is when an action is considered closed for reporting.

### Intake and Operational States

The five stages above are the reporting backbone. The operational tracker (`content-action-tracker.md`) adds two pre-brief intake states ahead of them — **Candidate** and **Next up** — used for triage and sequencing. These are not yet counted as Strategic Content Actions: consistent with the definition above, an item is counted from **Briefed** onward, when it warrants and has a brief. The tracker's **Gate** column records whether an intake item can start (Ready, Baseline needed, Technical track, or Blocked), and a **WIP limit of two** caps how many actions sit In Production at once. Technical-track items (e.g. a redirect pass) run in parallel and do not consume a WIP slot. The force-close terminal status, **Measured (closed without data)** (see Force-Close Rule), is also tracked here.

---

## Measurement Schedule and Enforcement

The "Live → Measured" transition is the most common point at which content reporting collapses. Without an explicit schedule, measured actions drift and the framework reverts to output-only tracking. The following mechanisms enforce the transition.

### Measurement Windows by Lever

| Lever | Window | Rationale |
|---|---|---|
| Organic Visibility | 60 days post-Live | SEO impact takes time to register in rankings and traffic |
| Conversion Performance | 30 days post-Live | Page-level conversion changes show in 2–4 weeks |
| Brand and Editorial | 60 days post-Live | Engagement and session data needs accumulation |
| Funnel Support | 30 days post-Live, or end of supported campaign | Tied to campaign window where applicable |

### Scheduled Measurement Slot

Measurement is a scheduled monthly batch, not a per-piece task.

- **Slot:** Last Friday of every month. Blocked in the calendar as a recurring half-day session.
- **What happens in the slot:** All actions in the pipeline tracker flagged as "Due for measurement" are reviewed. Outcome data is captured against the lever metric. Action status is moved to "Measured." Notes are added on what worked, what didn't, and any follow-up implications.
- **Output:** Updated pipeline tracker. Notes feed directly into the next quarterly outcome report.

The fixed monthly slot turns measurement from an interrupting task into a habit. Per-piece reminders are not used — they fragment attention and create noise.

### Pipeline Tracker

The single source of truth is `content-action-tracker.md` — a version-controlled markdown file in the brain, updated conversationally and committed via Claude Code. It replaces the earlier Google Sheet approach: the tracker lives alongside the skills, briefs, and audit it references, and every status change is captured in git history.

Columns:

| Column | Notes |
|---|---|
| ID | Unique identifier (SCA-00X) |
| Action | Piece or page name |
| Lever | One of four lever categories |
| Gate / track | Ready / Baseline needed / Technical track / Blocked |
| Owner | Person responsible |
| Status | Candidate / Next up / Briefed / In Production / In QA / Live / Measured / Measured (closed without data) |
| Live | Date published or deployed |
| Due | Measurement due date — Live date + lever window |
| Notes | Context, keyword targets, and outcome data captured at measurement |

Baselines are logged in the tracker's Baselines section before optimisation, so the pre/post comparison is clean. Outcome data is recorded against the relevant action at the monthly measurement slot.

Due dates are computed when an action moves to Live (Live date + the lever window) and recorded in the Due column. There is no auto-flagging formula — the monthly measurement slot is where due and overdue items are reviewed, and the state line at the top of the tracker carries the current counts and flags anything overdue.

### Force-Close Rule

At each quarterly review, any action that is Live, overdue for measurement by 60+ days, and has no documented reason for delay is force-closed:

- Status moves to "Measured (closed without data)"
- A note is logged explaining why measurement could not happen
- The lever's volume metric still counts the action as completed
- The lever's outcome metric excludes the action
- Repeated occurrences in the same lever signal that the lever's measurement design needs revisiting

Force-close exists so the pipeline never accumulates indefinite "Live but unmeasured" actions. It is deliberately a fallback — the monthly slot should prevent most force-closes.

---

## MVP Reporting

### Cadence
- **Monthly:** Volume report — pipeline stage summary, actions completed, actions in flight
- **Quarterly:** Outcome report — measured actions vs lever targets, lessons, what's next

### Audience
- Primary: Group Director of Marketing Performance, Digital Marketing Director
- Secondary: Marketing Managers (Spicers, Ardour & Independents, Bannisters) for actions touching their brands

### Format
- **Written executive summary:** narrative covering what shipped, what moved, and what's next — same format as campaign wrap reports per `campaign-workflow.md`. The monthly volume report and quarterly outcome report are generated directly from `content-action-tracker.md`.
- **Looker Studio dashboard (optional):** a leadership-facing visualisation layer for volume and lever-level outcome trends, added if and when reporting volume justifies it — no longer the tracker itself, since the markdown file is the source of truth.

### Monthly Volume Report — Minimum Contents
- Actions completed in period, by lever
- Actions in flight, by stage and lever
- Actions blocked or paused, with reason
- Owners and target publish dates for in-flight work

### Quarterly Outcome Report — Minimum Contents
- Measured actions in the period, by lever
- Pre/post performance against the lever's outcome metric
- Highest-impact action and lowest-impact action, with reasoning
- Lessons applied to the next quarter's brief priorities
- Pipeline outlook for the next quarter

---

## What's Out of MVP Scope

The following are deliberately not part of the MVP and are out of scope until the framework is bedded in:

- Real-time content dashboards
- Per-piece attribution modelling
- Multi-touch attribution across content and paid
- Revenue attribution at the article level for journal content
- Per-keyword tracking dashboards (use Ahrefs and GSC natively until volume justifies a custom dashboard)
- A/B testing infrastructure for landing pages
- Predictive scoring of content performance

These can be added once the MVP is delivering reliable monthly and quarterly reporting. Adding them earlier risks delaying the MVP and obscuring whether the simple framework actually works.

---

## Triage Guide for Stakeholders

When a stakeholder requests content work, the following questions determine whether it becomes a Strategic Content Action:

1. **Is there a defined business outcome?** If not, the request is either BAU service work or needs a strategic frame before it becomes an action.
2. **Does it warrant a brief?** If the work is large enough to need a brief, it is an action. If it doesn't, it isn't.
3. **Which lever does it sit under?** If it doesn't fit one of the four, either the lever framework needs to expand or the request isn't strategic content work.
4. **Who owns the outcome metric?** If the metric is owned by a campaign or by paid media, the request belongs in that channel's reporting, not here.

---

## Related Files
- `content-action-tracker.md` — the operational pipeline tracker; the live source of truth this framework's stages and measurement rules govern
- `content-action-workflow.md` — the tool-level execution workflow for the stages and measurement this framework defines
- `skills/content-action-brief-skill.md` — the brief template that defines whether work qualifies
- `skills/content-qa-skill.md` — the QA gate before "Live" status
- `skills/journal-skill.md`, `seo-content-skill.md`, `landing-page-skill.md` — skill files for actions in each lever
- `campaign-workflow.md` — distinct from this framework; covers campaign-level reporting
- `channel-strategy.md` — distinct from this framework; covers channel-level KPIs
- `projects/worldsapart-journal-build-scope.md` — the build that enables Brand & Editorial lever output
