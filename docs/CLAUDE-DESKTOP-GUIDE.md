# Using Claude for Website Edits

When you need to make changes beyond what the web CMS handles (design adjustments, new pages, layout fixes), Claude can do the technical work for you.

You describe what you want. Claude clones the repo, makes the edits, and pushes the changes live. You don't need to learn git or touch code.

---

## Quick Start: Install the Skill

I've created a skill that teaches Claude everything about the RFY website. Install it once and Claude will know how to help.

**On Mac, open Terminal and run:**
```bash
# Create the skills folder if it doesn't exist
mkdir -p ~/.claude/skills

# Clone the website repo (if you haven't already)
git clone https://github.com/vwieczorek/rfy-website ~/rfy-website

# Copy the skill
cp -r ~/rfy-website/skill/rfy-website ~/.claude/skills/
```

That's it. Claude now knows the site structure, where files live, and how to push changes.

---

## One-Time Setup: Connect GitHub

Before Claude can push changes to the live site, connect your GitHub account:

1. Open Claude Desktop
2. Go to the **Code** tab
3. Click the **...** menu, then **Connectors**
4. Enable **GitHub** and authorize the connection

---

## Making Changes

### Option 1: Use the Skill Directly

Type `/rfy-website` followed by what you want:

```
/rfy-website Update the main phone number to (317) 555-1234
```

```
/rfy-website Add a new staff member: Sarah Chen, Director of Clinical Services
```

```
/rfy-website The buttons are too bright green. Make them a deeper forest green.
```

```
/rfy-website Create a new page for summer programs with the same layout as services
```

### Option 2: Just Describe What You Want

Claude recognizes when you're talking about the website and loads the skill automatically:

> "I need to update the RFY website. The testimonials section looks cramped on mobile."

> "Can you fix the phone number on the RFY contact page?"

### Review and Approve

Claude shows you what it plans to change. In **Ask mode**, you approve each edit before it happens. You'll see exactly what's changing.

### Push Changes Live

When you're happy, tell Claude to push:

> "Commit and push these changes"

The site rebuilds automatically in about 30 seconds.

---

## What Claude Knows (from the Skill)

The skill teaches Claude:

- **Repository:** https://github.com/vwieczorek/rfy-website
- **Content files:** JSON files in `_data/` (staff, stats, testimonials, etc.)
- **Page templates:** `.njk` files in the root
- **Styling:** `css/style.css`
- **How to push:** Commit to `main`, auto-deploys to Cloudflare Pages

---

## Tips

**Use Ask mode when starting out.** You approve each change before it happens.

**Be specific.** "Make it look better" is vague. "Increase the headline font size" is clear.

**You can always undo.** Tell Claude to "revert the last commit" if something breaks.

**Ask questions.** "How does the homepage pull in statistics?" Claude can explain any part of the site.

---

## When to Use CMS vs Claude

| Task | CMS | Claude |
|------|-----|--------|
| Update phone number | Yes | |
| Add a staff photo | Yes | |
| Change button colors | | Yes |
| Add a new page | | Yes |
| Update a testimonial | Yes | |
| Fix mobile layout | | Yes |
| Update statistics | Yes | |
| Redesign a section | | Yes |

---

## Troubleshooting

**"I don't have access to that repository"**
Connect GitHub in Connectors. You also need collaborator access (Victor sets this up).

**Changes aren't showing on the live site**
Ask Claude "Did you push?" If yes, wait 60 seconds and hard refresh (Ctrl+Shift+R or Cmd+Shift+R).

**I made a mistake**
Tell Claude: "Revert the last commit"

**Skill not found**
Make sure you copied the skill folder to `~/.claude/skills/rfy-website/`

---

## Updating the Skill

If Victor updates the skill with new instructions:

```bash
cd ~/rfy-website
git pull
cp -r skill/rfy-website ~/.claude/skills/
```

---

## Getting Help

- CMS questions: See `EDITING-GUIDE.md`
- Technical details: See `README.md`
- Anything else: Ask Claude, or reach out to Victor
