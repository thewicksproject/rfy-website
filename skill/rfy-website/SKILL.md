---
name: rfy-website
description: Manage the Reach For Youth website. Clone the repo, edit content, fix layouts, create pages, and push changes live.
argument-hint: [what you want to change]
---

# Reach For Youth Website Management

You help manage the RFY website at https://rfy.thewicksproject.org

## Repository

- **Repo:** https://github.com/vwieczorek/rfy-website
- **Live site:** https://rfy.thewicksproject.org
- **Stack:** Eleventy static site, hosted on Cloudflare Pages
- **Auto-deploy:** Push to `main` triggers rebuild (about 30 seconds)

## Getting Started

If you don't have the repo cloned yet:

```bash
git clone https://github.com/vwieczorek/rfy-website
cd rfy-website
```

## Site Structure

Content lives in JSON files under `_data/`:

| File | Contains |
|------|----------|
| `site.json` | Organization info (phone, email, address, social links) |
| `staff.json` | Staff member profiles |
| `board.json` | Board member profiles |
| `stats.json` | Impact statistics shown on homepage |
| `testimonials.json` | Testimonials and quotes |
| `stories.json` | Success stories |
| `event.json` | Featured event details |
| `timeline.json` | History timeline on About page |
| `partners.json` | Funders and partners |
| `volunteerOpportunities.json` | Volunteer opportunities |
| `donationImpact.json` | Donation impact levels |
| `sponsorshipLevels.json` | Event sponsorship tiers |
| `mentalHealthServices.json` | Mental health program descriptions |
| `restorativePrograms.json` | Restorative justice program descriptions |

Page templates are `.njk` files in the root:
- `index.njk` - Homepage
- `about.njk` - About page
- `services.njk` - Services overview
- `contact.njk` - Contact page
- `donate.njk` - Donate page
- `volunteer.njk` - Volunteer page
- `events.njk` - Events page
- `success-stories.njk` - Stories page

Styling is in `css/style.css`.

Shared layouts and components are in `_includes/`.

## Common Tasks

### Update contact info
Edit `_data/site.json`. Phone numbers, email, addresses, and social links are all there.

### Add or update staff/board members
Edit `_data/staff.json` or `_data/board.json`. Each person has `name`, `title`, and optionally `image`.

### Update statistics
Edit `_data/stats.json`. The `hero` array shows on the homepage banner. The `impact` array shows elsewhere.

### Add a testimonial
Edit `_data/testimonials.json`. Add an object with `quote`, `name`, `role`, and `initial`.

### Change colors or fonts
Edit `css/style.css`. Brand colors are defined as CSS custom properties near the top.

### Create a new page
1. Create a new `.njk` file in the root
2. Add frontmatter with layout and title
3. Add content using Nunjucks templating
4. Link to it from the navigation in `_includes/header.njk`

## Pushing Changes

After making edits:

```bash
git add .
git commit -m "Brief description of changes"
git push
```

The site rebuilds automatically. Changes are live in about 30 seconds.

## When NOT to Use This Skill

For simple content updates (text, photos, stats, testimonials), the web CMS at https://rfy.thewicksproject.org/admin/ is faster. Use this skill for:

- Design changes (colors, layouts, spacing)
- Creating new pages
- Fixing display issues
- Bulk content updates
- Anything requiring code changes

## Task

$ARGUMENTS
