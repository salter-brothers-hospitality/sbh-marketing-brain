# Skill: Omnichannel Copy

## Purpose
Produce coordinated, on-brand copy for every channel in a campaign from a single Omnichannel Copy Brief (`skills/omnichannel-copy-brief-skill.md`). Covers paid social, paid search, programmatic, EDM, SEO pages, landing pages, journal/blog, destination guides, and organic social in one pass — including every text variation field each channel takes.

This skill does not replace the channel skills — it composes them. Each channel still obeys its own skill for format, structure, and limits. This skill's job is the layer above: holding one message steady while it changes shape across channels, keeping the voice correct for each one, and making sure every field of every channel is filled with distinctive copy rather than one line reworded.

---

## Core Principle

**One message, many expressions.**

The through-line stays constant across every channel: the core message, the proof points, the offer details, the CTA logic. The execution diverges per channel: format, length, register, structure, and the number of variations. Consistency of substance, divergence of form.

Three failure modes this skill exists to prevent:

1. **Drift.** Channels written separately pull apart. The hook mutates, the rate disagrees between the ad and the EDM, one channel invents a claim another doesn't make. Producing everything from one locked message architecture stops this.
2. **Voice flattening.** Channels written together collapse into a single voice. But the channels do not share one voice — paid, SEO, landing, EDM and organic take the sub-brand voice, while journal takes Worlds Apart voice. Producing together is efficient; it is also exactly when this gets missed.
3. **Lazy variation.** Responsive formats ask for many variations (15 Google headlines, 5 Meta primary texts). Writing one line and rewording it fifteen times technically fills the fields but starves the platform of anything to test. Every variation must be a genuinely different angle.

---

## The Voice Trap (read before producing)

This is the part most likely to go wrong. Get it right first.

- **Sub-brand voice** (Spicers / Ardour / Bannisters / Independents) governs: paid social, paid search, programmatic, SEO pages, landing pages, EDMs, organic social. The copy sounds like the property's brand.
- **Worlds Apart voice** governs the journal / blog (`/journal/`) — **always**, even when the piece is about a Spicers or Ardour property. A journal piece is what a luxury travel editor would write about a property, not what the property would write about itself. Do not slide into the sub-brand's tone.
- **Em dashes** are Ardour only. They never appear in a journal piece, even one about an Ardour property.
- **Worlds Apart is a platform, not a place.** Never write it as a destination you can visit or stay at.
- **Rick Stein at Bannisters** is always written in full, on every channel.
- **Cold vs retargeting** carry different messages. Cold / TOF is brand-first and evocative. Retargeting is offer-led with a clear CTA. The same campaign routinely runs both.
- **LinkedIn** is the C&E / corporate retreat / MICE channel — it usually sits at Worlds Apart or Ardour register, not leisure sub-brand tone. Confirm per brief.

---

## Channel Routing

Each channel defers to its governing skill for format and voice, and to `skills/channel-field-specs.md` for exact fields, limits, and how many variations to produce. This table is the map.

| Channel | Governing skill | Voice | Text fields (see specs sheet for limits) |
|---|---|---|---|
| Meta (FB/IG) | `ad-copy-skill.md` | Sub-brand | 5× primary text, 5× headline, 5× description |
| Google Ads (RSA) | `ad-copy-skill.md` | Sub-brand | 15× headline, 4× description, 2× path, business name |
| TikTok Ads | `ad-copy-skill.md` | Sub-brand | 5× ad caption, brand name |
| Pinterest Ads | `ad-copy-skill.md` | Sub-brand | 3–5× pin title, 3–5× pin description |
| LinkedIn Sponsored Content | `ad-copy-skill.md` | Worlds Apart / Ardour (C&E) | 3× intro text, 3× headline, 1× description |
| StackAdapt (native) | `ad-copy-skill.md` | Sub-brand | 3–5× headline, 3–5× body, brand name, CTA |
| Quantcast / Teads | `ad-copy-skill.md` | Sub-brand | Native: headline + body + brand + CTA. Display: copy baked into creative |
| EDM | `email-skill.md` | Sub-brand (WA for cross-brand) | Subject, preview, body, primary CTA |
| SEO page | `seo-content-skill.md` | Sub-brand | H1, H2s, body, meta title, meta description |
| Landing page | `landing-page-skill.md` | Sub-brand | Hero headline, subhead, inclusions, experience, CTA(s) |
| Journal / blog | `journal-skill.md` | **Worlds Apart** | Headline, dek, intro, body, soft CTA, meta |
| Destination guide | `destination-guide-skill.md` | Sub-brand present (WA for multi-brand) | Full template + meta |
| Organic social | `ad-copy-skill.md` + `channel-strategy.md` | Sub-brand | Per-platform caption + text-on-screen hook |

---

## Variation Coverage

Two rules, both enforced at production.

**Produce the full field set.** If a format takes 15 headlines, write 15. If Meta takes five primary texts, write five. Responsive and dynamic formats (Google RSA, Meta Advantage+, Performance Max) reward volume because the platform tests combinations, and a half-filled ad gets throttled — Google drops Ad Strength to Average or Poor and the ad runs less. The field counts are in `skills/channel-field-specs.md`.

**Make each variation distinct.** Fifteen headlines rewording one sentence is one headline submitted fifteen times. Each variation pulls a different angle from the proof-point bank so the platform has genuinely different material to test:
- Lead with a different proof point — the setting, the offer, the food, the season, the location, the occasion
- Vary the register — sensory, factual, occasion-led, practical
- Vary the length within the limit — some run short and punchy, some use the full count
- Never contradict another variation, and never invent a claim that isn't in the brief

Coverage check for any responsive set: is every proof point represented at least once across the variations, and is at least one variation leading on each of property/brand, offer, and location?

Distinctiveness stops at the facts. Variation lives in angle and phrasing, never in the offer — every variation states the same rate, the same inclusions, the same dates.

---

## Process

1. **Read the brief.** If the core message, proof points, or channel matrix are missing, stop — the brief is not ready. Send it back.

2. **Lock the message architecture before writing any channel.** Write these four things once, at the top of the kit, and pull from them for every channel afterwards. Nothing downstream introduces a new claim:
   - Core message (one sentence)
   - Hook
   - Proof-point bank (the named, factual details — this is the well every variation draws from)
   - CTA logic (what each temperature drives to: brand-first channels to discovery, conversion channels to the booking destination)

3. **Group the channels to reduce switching errors.** Produce all sub-brand-voice channels together, then switch deliberately to the journal piece in Worlds Apart voice. Within sub-brand channels, work cold-first then retargeting, so the brand message is set before the offer message leans on it.

4. **Produce each channel against its governing skill and the specs sheet.** Open the relevant skill's output format, and `channel-field-specs.md` for the field list and counts. Write every field. Draw each variation from the locked architecture, varying the angle per the Variation Coverage rules. Do not pad — if a category honestly has only eight strong headlines, the fix is a sharper angle, not filler.

5. **Apply the global non-negotiables at every line, not at review** (per `brands/brand-voice.md`): Australian spelling; no em dashes (Ardour excepted); no directive openers (Discover, Experience, Celebrate, Explore); no generic openers (Nestled, Situated, Set amidst); no hyperbole; no comparative or correlative structures (Whether X or Y, From X to Y, It's not X it's Y); no overused words (scrumptious, delectable, indulge, elevated, culinary journey, beauty); no prose ending on "Here..."; factual USPs over vague emotional claims.

6. **Run the cross-channel consistency pass** (see checklist). The hook is recognisable across channels; offer details are identical everywhere and inside every field set; CTAs point to the right destination; no channel contradicts another; voice is correct per channel; every field is filled and distinct.

7. **Hand off to QA.** The completed kit goes through `skills/content-qa-skill.md` before anything publishes.

---

## Output Format — The Copy Kit

A single structured document. It opens with the locked message architecture, then one clearly labelled section per channel. Each section header states channel, objective, temperature, and governing voice, so a reviewer can spot a voice slip at a glance. Within each section, every field is filled to its full variation count.

```
# [Campaign] — Copy Kit

## Message Architecture
Core message: [one sentence]
Hook: [the entry point]
Proof points: [the named, factual bank]
CTA logic: [where each temperature drives]

## Meta — Conversion — Cold — [sub-brand] voice
Primary text (5): 1. … 2. … 3. … 4. … 5. …
Headline (5): 1. … 2. … 3. … 4. … 5. …
Description (5): 1. … 2. … 3. … 4. … 5. …

## Google Ads RSA — [sub-brand] voice
Headlines (15): 1–15 …
Descriptions (4): 1–4 …
Paths (2): … / …
Business name: …

## TikTok Ads — [sub-brand] voice
Ad caption (5): …
Brand name: …

## Pinterest Ads — [sub-brand] voice
Pin title (3–5): …
Pin description (3–5): …

## LinkedIn Sponsored Content — Worlds Apart voice
Intro text (3): …
Headline (3): …
Description: …

## StackAdapt Native — [sub-brand] voice
Headline (3–5): …
Body (3–5): …
Brand name: … / CTA: …

## EDM — [sub-brand] voice
Subject (1–2): … / Preview: … / Body: … / Primary CTA: …

## SEO page — [sub-brand] voice
H1: … / H2s: … / Opening copy: … / Meta title: … / Meta description: …

## Journal — Worlds Apart voice
Headline: … / Dek: … / Intro: … / Soft CTA: … / Meta title: … / Meta description: …

## Organic social — [sub-brand] voice
[Platform]: caption + text-on-screen hook …
```

---

## Worked Example — Spicers Autumn 2026 (abridged)

Showing how one message holds while voice, format, and variation shift. The paid sets show distinctiveness; the journal piece shows the voice switch to Worlds Apart. A full kit fills every field — this abridges the counts to demonstrate the principle.

**Message Architecture**
- Core message: Autumn is the season the Spicers retreats are quietest and the food and gardens are at their best.
- Hook: the seasonal shift — cooler air, fewer people, cool-season produce; the Autumn Extras package for warm audiences.
- Proof points: stay window 1 March to 31 May 2026; Autumn Extras adds a three-course dinner for two, a bottle of wine on arrival, and a noon checkout; Stay Longer and Save; Early Bird; properties across Queensland and New South Wales.
- CTA logic: cold drives to the Autumn page; retargeting and EDM drive to the booking engine.

**Google Ads RSA — Spicers voice** *(8 of 15 headlines shown — note each leads on a different proof point)*
1. Spicers Retreats this Autumn *(brand + season)*
2. Autumn Extras at Spicers *(offer)*
3. Dinner for Two Included *(proof point)*
4. The Quiet Season at Spicers *(angle)*
5. Wine on Arrival, Noon Checkout *(proof point)*
6. Stay Longer and Save *(offer)*
7. Autumn Stays to 31 May *(window)*
8. Book Direct for Autumn Extras *(CTA)*

Descriptions (3 of 4 shown):
1. The Autumn Extras package adds dinner for two, wine on arrival, and a noon checkout. *(offer)*
2. Cooler mornings, longer lunches, the gardens turning over. The quietest the retreats get. *(experience)*
3. Book an Autumn stay direct on stays to 31 May. Stay longer across the season and save. *(practical / CTA)*

**Meta — Conversion — Cold — Spicers voice** *(3 of 5 primary texts — distinct angles)*
1. *(sensory)* Autumn settles over the retreats. Cooler mornings, longer lunches, the gardens turning over. The quietest the properties get all year.
2. *(occasion)* A quiet few days somewhere good. Autumn is the season to take the retreats slowly, before the weather turns.
3. *(location)* Spicers retreats sit across the Queensland hinterland and the New South Wales high country. Autumn is the season to have them mostly to yourself.

**EDM — Spicers voice**
- Subject: Autumn at Spicers. Extras included.
- Preview text: A three-course dinner, wine on arrival, a noon checkout.
- Body: Autumn is a quieter season at the retreats, and a good one to take slowly. Book a stay before 31 May and the Autumn Extras package adds a three-course dinner for two, a bottle of wine on arrival, and a noon checkout. Stay longer across the season and the savings grow with you.
- Primary CTA: See Autumn rates

**Journal — Worlds Apart voice** *(the deliberate shift)*
- Headline: Why Autumn is the quiet season worth booking
- Intro: Autumn is the season the southern retreats come into their own. Summer's crowds have gone, the produce has turned over, and three unhurried days somewhere like Spicers Peak Lodge or Spicers Vineyards Estate stretch further than they would in January. A few notes on where to go, and when.
- Soft CTA: Spicers Peak Lodge and Spicers Vineyards Estate both have Autumn availability. See rates and rooms on Worlds Apart.

*Why the sets work: every paid variation pulls a different proof point but states the same offer and dates. The journal piece keeps the same core message and proof points but reads as an editor's framing, not the property's — no Spicers host-voice, no offer-led push, platform-level throughout.*

---

## Quality Checklist

**Message consistency**
- [ ] Core message recognisable in every channel
- [ ] Proof points consistent — no channel invents a claim another doesn't make
- [ ] Offer details identical across every channel and inside every field set (rate, inclusions, both windows, conditions)
- [ ] Hook carries across channels without mutating into a different idea
- [ ] CTA destinations correct per channel and per temperature

**Variation coverage**
- [ ] Every channel's full field set is produced (15 Google headlines, 5 Meta variations per field, etc.) per `channel-field-specs.md`
- [ ] Each variation within a field is a distinct angle, not a reword
- [ ] Across each responsive set, every proof point appears at least once, and property/brand, offer and location each lead at least one variation
- [ ] Each field respects its character limit (verified against the specs sheet)

**Voice**
- [ ] Sub-brand voice on paid, SEO, landing, EDM, organic
- [ ] Worlds Apart voice on journal — even when the piece is about a sub-brand property
- [ ] LinkedIn at Worlds Apart / Ardour register for C&E, not leisure sub-brand tone
- [ ] Em dashes only on Ardour, and not in any journal piece
- [ ] Worlds Apart never written as a place
- [ ] Rick Stein at Bannisters in full, every channel
- [ ] Cold is brand-first; retargeting is offer-led, where the brief splits by temperature

**Global non-negotiables** (per `brands/brand-voice.md`)
- [ ] Australian spelling throughout
- [ ] No directive or generic openers
- [ ] No hyperbole or overused words
- [ ] No comparative or correlative structures
- [ ] No prose ending on "Here..."
- [ ] Factual USPs over vague emotional claims

**Handoff**
- [ ] Full kit run through `skills/content-qa-skill.md` before publish

---

## Related Files
- `skills/omnichannel-copy-brief-skill.md` — the input brief this skill works from
- `skills/channel-field-specs.md` — the field, limit, and variation-count reference for every channel
- `skills/ad-copy-skill.md` — paid and organic social copy
- `skills/email-skill.md` — EDM copy
- `skills/seo-content-skill.md` — SEO page copy
- `skills/landing-page-skill.md` — campaign and offer landing pages
- `skills/journal-skill.md` — journal / blog copy (Worlds Apart voice)
- `skills/destination-guide-skill.md` — destination guides
- `skills/content-qa-skill.md` — the pre-publish QA gate for the finished kit
- `skills/campaign-brief-skill.md` — the strategic brief upstream of the copy brief
- `brands/brand-voice.md` — cross-brand voice rules and global non-negotiables
- `content-reporting-framework.md` — multi-channel campaign copy usually sits under the Funnel Support lever
