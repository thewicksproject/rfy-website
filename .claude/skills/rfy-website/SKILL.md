---
name: rfy-website
description: Manage the Reach For Youth website (RFY, rfy.thewicksproject.org). Update content, edit styles, fix layouts, create pages, and push changes live.
argument-hint: e.g., "update the phone number" or "add a new staff member"
---

# Reach For Youth Website Management

You manage the RFY website at https://rfy.thewicksproject.org

## Repository

- **Repo:** https://github.com/thewicksproject/rfy-website
- **Local path:** `C:/Users/mbaker/OneDrive - Reach For Youth, Inc/BOARD/Marketing Committee/New Website/rfy-website`
- **Live site:** https://rfy.thewicksproject.org
- **Stack:** Eleventy static site, hosted on Cloudflare Pages
- **Auto-deploy:** Push to `main` triggers rebuild (about 30 seconds)

## Git Workflow

> **Important:** Bash on this machine completes silently. Always redirect output to a temp file and read it back.

### Pull latest before starting

```bash
git -C "C:/Users/mbaker/OneDrive - Reach For Youth, Inc/BOARD/Marketing Committee/New Website/rfy-website" pull origin main > C:/Users/mbaker/AppData/Local/Temp/gitpull.txt 2>&1
```
Then read `C:/Users/mbaker/AppData/Local/Temp/gitpull.txt` to confirm success.

### Commit and push after edits

```bash
git -C "C:/Users/mbaker/OneDrive - Reach For Youth, Inc/BOARD/Marketing Committee/New Website/rfy-website" add <file(s)> && \
git -C "C:/Users/mbaker/OneDrive - Reach For Youth, Inc/BOARD/Marketing Committee/New Website/rfy-website" commit -m "Brief description" && \
git -C "C:/Users/mbaker/OneDrive - Reach For Youth, Inc/BOARD/Marketing Committee/New Website/rfy-website" push origin main > C:/Users/mbaker/AppData/Local/Temp/gitpush.txt 2>&1
```
Then read `C:/Users/mbaker/AppData/Local/Temp/gitpush.txt` to confirm `main -> main`.

### If push is rejected (remote has new commits)

```bash
git -C "C:/Users/mbaker/OneDrive - Reach For Youth, Inc/BOARD/Marketing Committee/New Website/rfy-website" stash && \
git -C "C:/Users/mbaker/OneDrive - Reach For Youth, Inc/BOARD/Marketing Committee/New Website/rfy-website" pull --rebase origin main && \
git -C "C:/Users/mbaker/OneDrive - Reach For Youth, Inc/BOARD/Marketing Committee/New Website/rfy-website" stash pop && \
git -C "C:/Users/mbaker/OneDrive - Reach For Youth, Inc/BOARD/Marketing Committee/New Website/rfy-website" push origin main > C:/Users/mbaker/AppData/Local/Temp/gitpush.txt 2>&1
```

Always check for merge conflicts after stash pop. If conflicts exist, keep the upstream version (remote is authoritative).

---

## Site Structure

### Content Data (`_data/`)

| File | Contains |
|------|----------|
| `site.json` | Organization info (phone, email, address, social links) |
| `staff.json` | Staff member profiles |
| `board.json` | Board member profiles |
| `stats.json` | Impact statistics (homepage hero, impact sections, volunteer page) |
| `testimonials.json` | Testimonials and quotes |
| `stories.json` | Success stories |
| `featuredStory.json` | Featured story on success stories page |
| `event.json` | Featured event details |
| `timeline.json` | History timeline on About page |
| `partners.json` | Funders and partners |
| `volunteerOpportunities.json` | Volunteer opportunities |
| `donationImpact.json` | Donation impact levels |
| `sponsorshipLevels.json` | Event sponsorship tiers |
| `mentalHealthServices.json` | Mental health program descriptions |
| `restorativePrograms.json` | Restorative justice program descriptions |

### Page Templates

Root pages (`.njk` files):
- `index.njk` - Homepage
- `about.njk` - About page
- `services.njk` - Services overview
- `contact.njk` - Contact page
- `donate.njk` - Donate page
- `volunteer.njk` - Volunteer page
- `events.njk` - Events page
- `success-stories.njk` - Stories page

Service subpages (`services/`):
- `services/mental-health.njk` - Mental health services detail
- `services/restorative-justice.njk` - Restorative justice detail

### Styling

Main stylesheet: `css/styles.css`

Brand colors (CSS custom properties at top of file):
- `--color-primary: #00275B` — Navy (main brand)
- `--color-primary-light: #57088B` — Purple (accent)
- `--color-accent: #FF0778` — Pink (CTAs)
- `--color-accent-light: #72F2CE` — Teal
- `--color-accent-dark: #FF6D22` — Orange

Service card icon color modifiers:
- Default: navy→purple gradient
- `.service-card__icon--orange`: orange gradient (currently used on restorative justice)

### Layouts and Components (`_includes/`)

| File | Purpose |
|------|---------|
| `base.njk` | Base layout wrapper for all pages |
| `footer.njk` | Site footer |
| `icons.njk` | SVG icon definitions |
| `translate-modal.njk` | Language translation modal |

---

## Common Tasks

### Update contact info
Edit `_data/site.json`. Phone numbers, email, addresses, and social links are all there.

### Update statistics
Edit `_data/stats.json`.
- `hero` array: homepage banner stats
- `impact` array: other page sections
- `volunteer` array: volunteer page stats

### Add or update staff/board members
Edit `_data/staff.json` or `_data/board.json`. Staff images go in `images/staff/`.

### Add a testimonial
Edit `_data/testimonials.json`:
```json
{
  "quote": "This program changed my life.",
  "name": "Parent",
  "role": "Teen Court participant's mother",
  "initial": "P"
}
```

### Change colors or fonts
Edit `css/styles.css`. Brand colors are CSS custom properties near the top.

### Create a new page
1. Create a `.njk` file with frontmatter:
```
---
layout: base.njk
title: Page Title
---

Page content here...
```
2. Add navigation link in `_includes/base.njk` if needed.

---

## Task

$ARGUMENTS
