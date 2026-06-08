# Reference: Channel Field Specs

## Purpose
A single source of truth for the text fields, character limits, and variation counts each channel requires. Referenced by `skills/omnichannel-copy-skill.md` and `skills/ad-copy-skill.md` so the field inventory lives in one place rather than being repeated across skills.

**Maintenance note.** Platform specs change. The limits below were verified against platform documentation in June 2026. Treat the channel platform's own ad-spec page as the final word; re-check before a major build. The "Produce" column (how many variations to write) is our standard, not a platform limit.

A recurring distinction: **recommended / visible length** vs **hard maximum**. Most platforms accept more text than they display, then truncate behind a "See more" link that few people tap. Write to the recommended length, not the hard cap.

---

## Paid Social

### Meta (Facebook and Instagram) — single image / video
| Field | Limit | Produce | Notes |
|---|---|---|---|
| Primary text | 125 chars visible (hard cap far higher) | 5 | The hook must land inside the first 125 chars; everything after is hidden on mobile |
| Headline | 40 chars (≈27 shows in feed) | 5 | |
| Description | ≈30 chars | 5 | Often hidden on mobile — never put the CTA or a critical fact here |
| CTA | Button, from Meta's list | 1 | |

Carousel: each card takes its own headline and description. Advantage+ / dynamic creative tests the variations against each other, so fill all five per field.

### Google Ads — Responsive Search Ad (RSA)
| Field | Limit | Produce | Notes |
|---|---|---|---|
| Headline | 30 chars | 15 (min 3) | Google shows 2–3 at a time in any order — each must stand alone |
| Description | 90 chars | 4 (min 2) | Google shows 1–2 at a time |
| Display path | 15 chars | 2 | Cosmetic; need not match the real URL |
| Business name | 25 chars | 1 | |

Filling all 15 headlines and 4 descriptions is what earns a "Good" or "Excellent" Ad Strength; a half-filled ad gets throttled. Pin only when a headline must always appear (e.g. property name in position 1) — pinning everything turns an RSA back into a fixed ad. Performance Max uses the same asset limits plus a long headline (90 chars). Extensions, where used: callouts 25 chars, sitelink link text 25 chars (plus two 35-char descriptions), structured snippet values 25 chars.

### TikTok Ads — in-feed
| Field | Limit | Produce | Notes |
|---|---|---|---|
| Ad text / caption | 1–100 chars | 5 | Only ~4 lines show before "See more"; front-load the hook |
| Brand / app name | 2–20 chars | 1 | No emoji in this field |
| CTA | From TikTok's list | 1 | |

For catalogue / Search Ads, the ad title runs to 40 chars — write several to target different audiences and search intents.

### Pinterest Ads
| Field | Limit | Produce | Notes |
|---|---|---|---|
| Pin title | 100 chars | 3–5 | Treated as a search headline — front-load the keyword |
| Pin description | 500 chars | 3–5 | First 50–60 chars matter most; keyword-rich, reads like a mini summary |
| CTA | Button | 1 | |

### LinkedIn — single image Sponsored Content
| Field | Limit | Produce | Notes |
|---|---|---|---|
| Introductory text | 150 chars recommended (600 max) | 3 | The visible hook |
| Headline | 70 chars recommended (200 max) | 3 | Truncates with no "see more" — keep it under 70 |
| Description | ≈70 chars (300 max) | 1 | Only shows on certain placements / Audience Network |
| CTA | From LinkedIn's list | 1 | |

LinkedIn is the C&E, corporate retreat, and MICE channel for the portfolio — voice usually sits at Worlds Apart or Ardour register rather than leisure sub-brand tone. Confirm per brief.

---

## Programmatic

### StackAdapt — native
| Field | Limit | Produce | Notes |
|---|---|---|---|
| Headline / title | 55 chars (min 15) | 3–5 | StackAdapt's own guidance favours ≤50 |
| Description / body | 120 chars (min 25) | 3–5 | Should summarise what the click delivers |
| Brand name / "Sponsored by" | 25 chars | 1 | |
| CTA text | 10 chars | 1 | |

### Quantcast and Teads — programmatic display and native
Native units follow a headline + body + brand + CTA pattern close to StackAdapt's; confirm exact field limits per placement and creative type in the DSP, as they vary. Standard display banners carry minimal or no separate copy — messaging is baked into the creative, so this is a design task more than a copy task. Brief copy only for native and in-read placements.

---

## Owned and Earned

### EDM (email)
| Field | Limit | Produce | Notes |
|---|---|---|---|
| Subject line | <50 chars | 1–2 | One emoji permitted for Ardour only |
| Preview text | 40–90 chars | 1 | Complements the subject, does not repeat it |
| Body | — | 1 | Key message / offer by the second sentence |
| Primary CTA | — | 1 | One primary; a secondary CTA at the foot is fine |

Governed by `skills/email-skill.md`.

### SEO page
| Field | Limit | Produce | Notes |
|---|---|---|---|
| H1 | — | 1 | Primary keyword, natural — not a tagline |
| H2s | — | as needed | Secondary keywords and supporting intent |
| Body | — | — | Written line by line |
| Meta title | <60 chars | 1 | Keyword-first |
| Meta description | <155 chars | 1 | Benefit-led, soft CTA |

Governed by `skills/seo-content-skill.md`.

### Landing page
Structural rather than character-limited: hero headline, sub-headline / intro, offer / inclusions, experience section, property context, CTA section, optional FAQ. Governed by `skills/landing-page-skill.md`.

### Journal / blog
| Field | Limit | Produce | Notes |
|---|---|---|---|
| Headline | — | 1 | Editorial, not a keyword string |
| Dek | — | 1 | Used in cards and as meta description fallback |
| Body | — | — | Prose-led, H2/H3 where genuine sections |
| Soft CTA | — | 1 | Editorial, e.g. "See availability at [property]" |
| Meta title | <60 chars | 1 | Reads as an editorial title |
| Meta description | <155 chars | 1 | Benefit-led |

Governed by `skills/journal-skill.md` — **Worlds Apart voice**.

### Destination guide
Full template per `skills/destination-guide-skill.md`: hero (H1 + descriptor), region snapshot, getting here, experiences by category, insider picks, where to stay, practical guide, FAQ, plus title tag (≤60) and meta description (≤155).

### Organic social
| Platform | Field | Limit | Notes |
|---|---|---|---|
| Instagram / Facebook | Caption | 2,200 max (≈125 visible) | Hook in the first line |
| TikTok | Caption | up to 2,200 | Hook in the first line; supports the video, not competes with it |
| Pinterest | Title / description | 100 / 500 | As per Pinterest Ads |
| Reels / TikTok / Stories | Text-on-screen hook | — | The hook the audience actually reads — primary copy for video |

Governed by `skills/ad-copy-skill.md` (organic notes) and the organic principles in `channel-strategy.md` (Reels-first, strong hooks, Jacquemus-style originality).

---

## Sources (verify before a major build)
- Google Ads Help — responsive search ads and Performance Max asset specs
- Meta / Facebook Business Help — ad format and text specifications
- TikTok Ads Manager — in-feed and catalogue ad specifications
- Pinterest Business — Pin and ad specifications
- LinkedIn Marketing Solutions Help — Sponsored Content specifications
- StackAdapt / Sharethrough support — native display creative specs
- For Quantcast and Teads, confirm in the DSP per placement
