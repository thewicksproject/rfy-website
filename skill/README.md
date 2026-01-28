# RFY Website Skill for Claude

This skill teaches Claude how to manage the Reach For Youth website.

## Installation

Copy the `rfy-website` folder to your Claude skills directory:

**Mac:**
```bash
cp -r rfy-website ~/.claude/skills/
```

**Windows (PowerShell):**
```powershell
Copy-Item -Recurse rfy-website $env:USERPROFILE\.claude\skills\
```

If the `~/.claude/skills/` directory doesn't exist, create it first.

## Usage

Once installed, you can invoke the skill in Claude Desktop:

1. Open Claude Desktop
2. Go to the **Code** tab
3. Type `/rfy-website` followed by what you want to do

**Examples:**

```
/rfy-website Update the main phone number to (317) 555-1234
```

```
/rfy-website Add a new staff member: Sarah Chen, Director of Clinical Services
```

```
/rfy-website The testimonials section looks cramped on mobile. Add more spacing.
```

```
/rfy-website Create a new page for summer programs
```

Or just describe what you want in plain language. Claude will recognize when this skill applies and load it automatically.

## What the Skill Knows

- Repository location and how to clone it
- Site structure (which files control what)
- How to edit content, styles, and layouts
- How to commit and push changes
- When to use the web CMS vs Claude

## Updating the Skill

To get the latest version, pull the repo and copy the skill folder again:

```bash
cd ~/path/to/rfy-website
git pull
cp -r skill/rfy-website ~/.claude/skills/
```
