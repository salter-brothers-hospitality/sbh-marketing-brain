# Skill: Omnichannel Copy Brief

## Purpose
The single input document for producing coordinated copy across every channel in a campaign or initiative. One brief in, all channels out.

This brief sits between two documents that already exist. The campaign brief (`skills/campaign-brief-skill.md`) answers *what are we running, why, on what budget, against what KPIs*. This copy brief answers *what does every line need to say, and in what voice, on each channel*. It is the source of truth the writer (or Claude, using `skills/omnichannel-copy-skill.md`) works from to produce the full copy kit.

Use it whenever a single message needs to land across more than one channel — a seasonal campaign, a property opening, an offer push, an always-on refresh. For single-channel work, the relevant channel skill on its own is enough; this brief is for coordination.

---

## Output Format
A single multi-section document. Fillable. Tables where data is cleaner, prose where context is needed. No padding.

The test for readiness: **if the core message, the proof points, or the channel matrix cannot be filled, the copy is not ready to produce.** Everything else can be refined in production; those three cannot.

---

## Brief Template

---

### Omnichannel Copy Brief

**Campaign / initiative:** [name]

---

#### 1. Snapshot

| Field | Detail |
|---|---|
| Brand / property(ies) |  |
| Linked campaign brief | [file or "standalone"] |
| Owner |  |
| Brief date |  |
| Copy due |  |
| Live date |  |

---

#### 2. The Through-Line

This is the part that holds every channel together. Fill it before anything else.

**Core message** *(one sentence — the single thing every channel must land, regardless of format. Channel-agnostic. If it reads like an ad headline, it is too specific; if it reads like a brand value, it is too vague.)*

**Hook / angle** *(the concrete entry point: the setting detail, the seasonal moment, the offer, the opening. What makes someone stop.)*

**Proof points** *(3–6 specific, factual, named details every channel draws from. These prevent vagueness and stop the copy drifting between channels. Name actual things.)*
1.
2.
3.

**Reason to act now** *(seasonal peg, offer window, opening date, limited availability — kept subtle, never "don't miss out")*

---

#### 3. Audience

**Primary persona:** Julie / Sam / The Celebrant / The Coastal Escapee / The Character Seeker

**Temperature split** *(does the message change by audience temperature? If yes, state each. Cold is brand-first and evocative; retargeting is offer-led. The same campaign routinely carries two messages.)*
- **Cold / TOF:**
- **Retargeting / warm:**

---

#### 4. Offer / Inclusions *(if applicable — skip for pure brand work)*

| Field | Detail |
|---|---|
| Offer name |  |
| Inclusions | *(exhaustive and specific — these become the proof points for conversion channels)* |
| Rate / from-price |  |
| Booking window |  |
| Stay window |  |
| Conditions / blackouts |  |

---

#### 5. Voice

**Governing brand voice:** Spicers / Ardour / Bannisters / Worlds Apart / Independents

**Voice exceptions to flag for this brief** *(tick what applies — these are the things that break when one writer produces all channels at once)*
- [ ] Em dashes in play — Ardour only, and never in any journal piece even for an Ardour property
- [ ] A journal / blog piece is in scope — it takes Worlds Apart voice, not the sub-brand voice, even when it is about a sub-brand property
- [ ] Worlds Apart appears as publisher or platform — it is a platform, not a place; never written as a destination
- [ ] Rick Stein at Bannisters features — always in full, every channel
- [ ] Cross-brand offer — defaults to Worlds Apart voice rather than a single sub-brand

---

#### 6. Channel Matrix

The spine of the brief. One row per channel in play. Drop rows that do not apply. Field counts and character limits for each channel live in `skills/channel-field-specs.md` — this matrix only decides which channels run and how.

| Channel | In play | Objective | Audience temp | Governing skill | Destination / CTA |
|---|---|---|---|---|---|
| Meta (FB/IG) | | awareness / consideration / conversion | cold / retargeting | ad-copy-skill | |
| Google Ads (RSA) | | | | ad-copy-skill | |
| TikTok Ads | | | | ad-copy-skill | |
| Pinterest Ads | | | | ad-copy-skill | |
| LinkedIn Sponsored Content | | | | ad-copy-skill | |
| StackAdapt (native) | | | | ad-copy-skill | |
| Quantcast / Teads | | | | ad-copy-skill | |
| EDM | | | | email-skill | |
| SEO page | | | | seo-content-skill | |
| Landing page | | | | landing-page-skill | |
| Journal / blog | | | | journal-skill | |
| Destination guide | | | | destination-guide-skill | |
| Organic social | | | | ad-copy-skill (organic notes) | |

---

#### 7. Must Mention / Must Avoid

**Must mention** *(named properties, dishes, rooms, partners, room counts, dates — the specific texture)*
-
-

**Must avoid** *(embargoes, sensitivities, the overused-words list, comparative or correlative structures, any positioning not yet live)*
-
-

---

#### 8. Assets

| Channel | Assets available / required | Note |
|---|---|---|

*(Defer to each channel skill for exact sizes and specs. This section is to flag gaps, not to spec production.)*

---

*Brief approved by: ____________________  Date: __________*

---

## Quality Checklist (for the brief itself)
- [ ] Core message is one sentence and channel-agnostic — it is not an ad headline and not a brand value
- [ ] At least three proof points, each a specific named detail (a property, a dish, a room count, a date) — not a feeling
- [ ] Governing voice named, and every relevant voice exception ticked in section 5
- [ ] Channel matrix complete — every channel in play has an objective, an audience temperature, and a destination
- [ ] If the message differs cold vs retargeting, both versions are stated
- [ ] Offer details complete where an offer applies (inclusions, rate, both windows, conditions)
- [ ] Must Mention includes at least one specific named detail
- [ ] No field left blank without an explanation

---

## Related Files
- `skills/omnichannel-copy-skill.md` — the production skill that turns this brief into the full copy kit
- `skills/channel-field-specs.md` — the fields, limits, and variation counts each channel in the matrix requires
- `skills/campaign-brief-skill.md` — the strategic/operational brief this copy brief sits beneath
- `skills/ad-copy-skill.md`, `email-skill.md`, `seo-content-skill.md`, `landing-page-skill.md`, `journal-skill.md`, `destination-guide-skill.md` — the channel skills the matrix routes to
- `brands/brand-voice.md` — cross-brand voice rules and global non-negotiables
- `brands/icp-and-audience.md` — persona definitions for section 3
- `content-reporting-framework.md` — multi-channel campaign copy usually sits under the Funnel Support lever
