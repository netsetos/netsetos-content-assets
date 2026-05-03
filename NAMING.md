# Filename Naming Convention

Every asset in this repo follows a strict naming pattern. The rules are pedantic on purpose — they make Drive-style search work, and they let anyone (Sart, Tanu, future content help) find any asset in seconds.

## The pattern

```
<CHANNEL_PREFIX>_<KEBAB_CASE_SLUG>.<extension>
```

For multi-channel files:

```
<CHANNEL>_<CHANNEL>_<CHANNEL>_<KEBAB_CASE_SLUG>.<extension>
```

## Channel prefixes

| Prefix | Channel | Workspace |
|---|---|---|
| `WA` | WhatsApp Community — broad tech | Netsetos Daily |
| `HQ-WA` | WhatsApp Community — GenAI cohort | Netsetos HQ |
| `TG` | Telegram broadcast | Netsetos Daily |
| `X` | Twitter / X | Netsetos Daily |
| `LI-Sart` | LinkedIn — Sart's profile | Either workspace |
| `LI-Tanu` | LinkedIn — Tanu's profile | Either workspace |
| `LI-Co` | LinkedIn — Netsetos company page | Either workspace |
| `DC` | Discord | Either workspace |
| `YT` | YouTube Community Tab | Either workspace |
| `MD` | Medium | Netsetos Daily |
| `RD` | Reddit | Netsetos Daily |
| `WEB` | netsetos.com | Either workspace |

## Multi-channel order convention

When chaining prefixes for a file used across multiple channels, **always use this order**:

```
WhatsApp → Telegram → Twitter → LinkedIn → Discord → YouTube → Medium → Reddit → Web
```

This way, "all WhatsApp assets" search finds files starting with `WA_*` AND files like `WA_TG_X_*` (because `WA` is still the leading token).

## Slug rules

After the prefix, the slug describes the content:

- **Lowercase only** — no caps mid-slug
- **Kebab-case** — words separated by single dashes
- **No spaces, ever** — they break URL hotlinking
- **No special characters** except `-` (between words) and `_` (between prefix and slug, and between channel prefixes)
- **Be specific but brief** — `cursor-3-multi-repo` is better than `cursor-3-agents-window-multi-root-workspace` AND better than just `cursor`
- **Include version suffix if it matters** — `Roadmap-2026-v1.pdf`, `Roadmap-2026-v2-preview.pdf`

## Examples by post type

### Daily brief image (one image, multiple channels)

```
WA_TG_X_cursor-3-multi-repo.gif       ✅
WA_TG_X_cursor-3-multi-repo-static.png ✅ (static fallback)
```

### LinkedIn-only carousel

```
LI-Sart_5-rag-mistakes-carousel.pdf   ✅
LI-Tanu_curriculum-14-modules.pdf     ✅
```

### Cross-shared from personal to company page

```
LI-Sart_LI-Co_token-tax-image.png     ✅
```

### YouTube Community Tab post (image asset)

```
YT_whatsapp-launch-announce.png       ✅
YT_cohort-1-poll-image.png            ✅
```

### Brand library (no day prefix needed)

```
00-brand-library/tiles-linkedin-services/Tile-1_GenAI-Cohort.png     ✅
00-brand-library/roadmap-pdfs/Netsetos-GenAI-Roadmap-2026-v1.pdf     ✅
00-brand-library/carousels/Day3_Sart-RAG-Mistakes-Carousel.pdf       ✅
```

## Bad examples (don't do these)

```
my image.gif                          ❌ spaces
WhatsappBrief1.png                    ❌ no slug, ambiguous
2026-05-04_image_final_FINAL_v3.gif   ❌ no channel prefix, redundant suffixes
WA_post.png                           ❌ slug too generic
WA_TG_post-about-the-new-cursor-3-agents-window-multi-root-workspace-feature.gif  ❌ slug too long
LI_some-post.png                      ❌ ambiguous (Sart? Tanu? Company?)
```

## When in doubt

If you're staring at a file and not sure how to name it:

1. Which channel(s) is this going to? → that's your prefix(es)
2. What's this post about in 2-4 words? → that's your slug
3. What's the file extension? → that's done

If a name is still over 60 characters total, the slug is too long. Shorten.
