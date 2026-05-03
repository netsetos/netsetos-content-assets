# Netsetos Content Assets

Single source of truth for all Netsetos visual content. Public repo so files can be hotlinked anywhere — Notion, WhatsApp, Twitter, LinkedIn, Discord — without re-uploading per channel.

> **Purpose:** This repo isn't code. It's a CDN. Files live here so they have one canonical URL each, and so we can find any past asset by date or channel without a Drive search.

---

## How URLs work (the whole reason this repo exists)

Once a file is committed and pushed to `main`, it has a permanent direct-image URL:

```
https://raw.githubusercontent.com/<your-username>/netsetos-content-assets/main/<path-to-file>
```

That URL works as a real `<img src=...>` everywhere — Notion auto-embeds, WhatsApp/Telegram preview it, Twitter renders it, LinkedIn uses it.

**Example:**

File on disk: `2026-05-may/W1-may-4-10/Day-001-Mon-May-4/WA_TG_X_cursor-3-multi-repo.gif`

Hotlink URL: `https://raw.githubusercontent.com/<your-username>/netsetos-content-assets/main/2026-05-may/W1-may-4-10/Day-001-Mon-May-4/WA_TG_X_cursor-3-multi-repo.gif`

> **⚠️ Replace `<your-username>` with your actual GitHub username after first push.**
> If the repo is owned by a GitHub organization, replace with the org name instead.

---

## Folder structure

```
.
├── 00-brand-library/                    Evergreen, reused across many posts
│   ├── tiles-linkedin-services/         5 LinkedIn Services page tiles
│   ├── roadmap-pdfs/                    GenAI Engineering Roadmap (v1, future v2…)
│   ├── carousels/                       LinkedIn carousel PDFs (Day 2, Day 3, future)
│   └── logos-banners/                   Logos, banner art, channel art
│
├── 2026-05-may/                         Monthly folder
│   └── W1-may-4-10/                     Weekly folder (matches Notion week-of)
│       ├── Day-001-Mon-May-4/           Day folder (Day# is launch day, not calendar day)
│       │   ├── WA_TG_X_cursor-3-multi-repo.gif
│       │   ├── WA_TG_X_cursor-3-multi-repo-static.png
│       │   └── README.md                Day's content map (what posts where)
│       ├── Day-002-Tue-May-5/
│       ├── Day-003-Wed-May-6/
│       ├── Day-004-Thu-May-7/
│       ├── Day-005-Fri-May-8/
│       ├── Day-006-Sat-May-9/
│       └── Day-007-Sun-May-10/
│
├── README.md                            This file
├── NAMING.md                            Filename channel-prefix legend
└── .gitignore                           Keep working files out of the repo
```

---

## Filename convention

Every file starts with a **channel prefix** so you can search the whole repo for "all WhatsApp posts" or "all LinkedIn-Sart posts" instantly.

| Prefix | Channel |
|---|---|
| `WA` | WhatsApp Community (Netsetos Daily — broad tech) |
| `HQ-WA` | WhatsApp Community (Netsetos HQ — GenAI cohort) |
| `TG` | Telegram broadcast |
| `X` | Twitter / X |
| `LI-Sart` | LinkedIn — Sart's personal profile |
| `LI-Tanu` | LinkedIn — Tanu's personal profile |
| `LI-Co` | LinkedIn — Netsetos company page |
| `DC` | Discord |
| `YT` | YouTube Community Tab |
| `MD` | Medium |
| `RD` | Reddit |
| `WEB` | netsetos.com |

When a file goes to multiple channels, **chain the prefixes with underscores** in the order: WhatsApp → Telegram → Twitter → LinkedIn → others.

**Examples:**

- `WA_TG_X_cursor-3-multi-repo.gif` — same GIF used on WhatsApp, Telegram, and Twitter
- `LI-Sart_5-RAG-mistakes-carousel.pdf` — Sart's Day 3 LinkedIn carousel only
- `LI-Sart_LI-Co_token-tax-image.png` — Sart's profile + company reshare

After the prefix, use **kebab-case slugs** (lowercase, dashes between words). No spaces. No special characters except `-` and `_`.

Full convention details in [`NAMING.md`](./NAMING.md).

---

## How to add a new asset

### Path A — Git CLI (Sart's primary path)

```bash
cd ~/code/netsetos-content-assets

# Drop the file into the right folder, e.g.
cp ~/Downloads/Day2_paper-sycophantic-llms.gif \
   2026-05-may/W1-may-4-10/Day-002-Tue-May-5/WA_TG_X_sycophantic-llms.gif

# Commit and push
git add .
git commit -m "Day 2 — Sycophantic LLMs paper image (WA + TG + X)"
git push origin main
```

Within 30 seconds the file is hotlinkable at `raw.githubusercontent.com/...`.

### Path B — GitHub web UI (Tanu's primary path)

1. Go to `github.com/<your-username>/netsetos-content-assets`
2. Navigate into the right Day folder
3. Click **Add file → Upload files**
4. Drag the file in
5. Scroll down, write a commit message ("Day 2 sycophantic LLMs image"), click **Commit**

Same outcome, no command line.

---

## How to use a hotlink in Notion

1. Once a file is committed, click it on GitHub
2. Click the **Raw** button (top-right of the file preview)
3. Copy the URL from your browser's address bar — it'll start with `raw.githubusercontent.com/`
4. In Notion, paste this URL on a new line in the page body
5. Notion auto-detects the image and renders it inline (animations work for GIFs)

Also paste the same URL into the row's `Source URL` property in the Content Calendar so you can find it later.

---

## Day-folder content map (README.md inside each day)

Every day folder has its own `README.md` describing which posts use which files. Example structure:

```markdown
# Day-001 — Mon May 4, 2026

## Posts shipping today

| Time | Channel | Post title | File used |
|---|---|---|---|
| 8:00 AM IST | X | Cursor 3.0 multi-repo test | WA_TG_X_cursor-3-multi-repo.gif |
| 9:00 AM IST | WhatsApp Daily | Tool — Cursor 3.0 Agents Window | WA_TG_X_cursor-3-multi-repo.gif |
| 9:05 AM IST | Telegram | Tool — Cursor 3.0 Agents Window | WA_TG_X_cursor-3-multi-repo.gif |
```

The README lives next to the assets, so opening any day-folder shows you the full picture in 5 seconds.

---

## What lives in `00-brand-library/`

Evergreen assets that get **reused across many posts and many days**:

- **`tiles-linkedin-services/`** — 5 tiles uploaded to LinkedIn Services page. Reused as banner images, Featured Section assets, and standalone post visuals.
- **`roadmap-pdfs/`** — GenAI Engineering Roadmap PDFs. The primary "free lead magnet" — referenced in dozens of posts.
- **`carousels/`** — LinkedIn carousel PDFs that get pinned, referenced, or reshared multiple times (Day 2 Tanu curriculum, Day 3 Sart RAG mistakes).
- **`logos-banners/`** — Netsetos logo files, channel banner art, profile pictures.

Files in this folder don't get duplicated into day-folders. They're shared — referenced from any day's README that uses them.

---

## What does NOT belong in this repo

- Source code (Python build scripts, LaTeX, etc.) — separate repo
- Conversation drafts, content calendar entries, post copy — those live in Notion
- Customer data, financial info, anything sensitive — separate private repo if needed
- Working files (.psd, .fig, .ai) — separate Drive folder, only commit final exports here
- Anything over 100MB — GitHub will reject it; use Drive for large videos

---

## Public repo notes

This repo is **public** because:
- All marketing assets go on public channels anyway (LinkedIn, Twitter, WhatsApp Community)
- Public repos give us free `raw.githubusercontent.com` hotlinks
- Public repos are free forever
- No one's watching what you commit to a marketing assets repo — there's no embarrassing version history

What you should NOT put in here:
- Anything you wouldn't paste in a public LinkedIn post
- Internal financial data
- Anything tagged "draft — don't share yet" (drafts go in a separate private repo if needed)

---

## Maintenance

- **Weekly:** during Sunday batch session, ensure all of next week's assets are committed and the corresponding Notion `Source URL` fields are updated
- **Monthly:** when starting a new month, create the next monthly folder (`2026-06-june/`) and the first week's structure inside it. Use the same template as `2026-05-may/`.
- **Quarterly:** review `00-brand-library/` and prune assets that are no longer referenced anywhere

---

*Owned by Sart Kumar & Tanu Varshney · Netsetos Technologies LLP · Hyderabad, India*
