# DahShu IDSWG Website

The official website of the DahShu Innovative Design Scientific Working Group. Built with [Quarto](https://quarto.org) and deployed to GitHub Pages.

**Live site:** https://idswg.github.io (or your custom domain)

---

## Prerequisites

Install [Quarto](https://quarto.org/docs/get-started/) — that's the only requirement.

---

## Local Preview

```bash
# Clone the repo
git clone https://github.com/your-org/idswg_website.git
cd idswg_website

# Start local preview (opens in browser automatically, live-reloads on save)
quarto preview
```

---

## How to Update Common Content

### Update the KOL Lecture Schedule

Open `events.qmd` and find the `KOL_DATA` array near the top of the HTML block. Each entry is one object:

```js
{ month: "January", speaker: "Name", affil: "Institution", topic: "Talk title" }
```

Leave `topic: ""` for talks not yet confirmed — it renders as "Topic forthcoming."

At the start of each year, replace the array entries with the new schedule.

### Add a Publication

Open `publications.qmd`. Find the appropriate section (peer-reviewed, books, in-progress) and add a new `<li>` following the existing pattern:

```html
<li>
  <span class="pub-year">2026</span><br/>
  <strong>Title of Paper</strong><br/>
  Author list. <em>Journal Name</em> (2026).<br/>
  <a href="https://doi.org/..." target="_blank">doi:... →</a>
</li>
```

### Update Leadership

Open `about.qmd`. Each leader has a `.leader-card` div. Update the name, title, affiliation, responsibilities, and email link. The Chair card has the extra class `leader-chair`.

Also update the initials and color in the avatar circle (`<div class="avatar">`) if the person changes.

### Add a News Post

Create a new `.qmd` file in `news/posts/` following this naming convention:

```
news/posts/YYYY-MM-DD-short-title.qmd
```

The file needs this YAML front matter:

```yaml
---
title: "Your Post Title"
date: 2026-01-15
description: "A one-sentence summary for the listing page."
categories: [Publication, Award, Event, Leadership]
---
```

Then write the post content in Markdown below. The news listing page (`news/index.qmd`) picks it up automatically.

### Update the Master Protocol Repository

Open `repository.qmd` and find the `PROTOCOLS` array in the JavaScript block. Add or edit entries following the existing structure — each object has `name`, `type`, `disease`, `phase`, `sponsor`, `year`, `status`, and `description` fields.

### Update the Regulatory Watch Page

Open `regulatory.qmd` and add new guidance documents to the `resource-grid` section. Follow the existing `.resource-card` pattern with the correct `resource-type` label (FDA Guidance, EMA Guidance, etc.).

---

## Deployment

Deployment is **automatic**. Every push to the `main` branch triggers the GitHub Actions workflow (`.github/workflows/publish.yml`), which renders the site and publishes it to the `gh-pages` branch.

To deploy manually (e.g., for testing):

```bash
quarto publish gh-pages
```

### Setting Up GitHub Pages (First Time)

1. Push the repo to GitHub
2. Go to Settings → Pages → Source: select **Deploy from branch** → branch: **gh-pages**
3. The first automated deploy will create the `gh-pages` branch

### Custom Domain

To use a custom domain (e.g., `idswg.org`):
1. Replace the contents of `CNAME` with your domain (one line, no `https://`)
2. Configure your domain's DNS to point to GitHub Pages (see [GitHub docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site))

---

## File Structure

```
idswg_website/
├── .github/workflows/publish.yml   # Auto-deployment
├── _quarto.yml                      # Site config, navbar, footer
├── styles.css                       # All custom styles
├── _includes.html                   # Skip link, back-to-top, JSON-LD
├── index.qmd                        # Homepage
├── about.qmd                        # Leadership and structure
├── subteams.qmd                     # All sub-teams
├── publications.qmd                 # Papers and presentations
├── events.qmd                       # KOL schedule + archive
├── statbridge.qmd                   # StatBridge program
├── resources.qmd                    # White papers, tools, external links
├── glossary.qmd                     # Term definitions
├── timeline.qmd                     # Group history
├── repository.qmd                   # Master protocol repository
├── regulatory.qmd                   # Regulatory guidance watch
├── join.qmd                         # Join / contact
├── news/
│   ├── index.qmd                    # News listing page
│   └── posts/                       # Individual news posts (add here)
├── images/
│   ├── IDSWG_Banner.png
│   └── IDSWG_Logo.png
├── 404.qmd
├── robots.txt
├── .nojekyll
└── CNAME
```

---

## Analytics

The site is configured for [Plausible Analytics](https://plausible.io) (privacy-friendly, GDPR-compliant, no cookie consent required). To activate:

1. Create a Plausible account and add your domain
2. In `_quarto.yml`, uncomment the analytics section and replace `your-domain.com` with your actual domain

---

## Questions?

Contact Bryan McComb or Alex Sverdlov — contact details on the About page.

---

## Maintenance Cheat Sheet (Quick Reference)

### The 20% of tasks that cover 80% of updates:

| Task | File to Edit | What to Change |
|------|------|------|
| New KOL speaker added | `events.qmd` | Find `KOL_DATA` array, add `{ month:"...", speaker:"...", affil:"...", topic:"..." }` |
| New publication | `publications.qmd` | Add `<li>` to the relevant `<ul class="pub-list">` section |
| New news post | Create `news/posts/YYYY-MM-DD-title.qmd` | Copy any existing post, update YAML + content |
| Leadership change | `about.qmd` + `join.qmd` | Edit the relevant `.leader-card` div in about.qmd; update the contact table row in join.qmd |
| Sub-team lead change | `subteams.qmd` + `subteam-pages/[name].qmd` | Update the `subteam-leads` div and the sub-team page |
| App URL (repository) | `repository.qmd` | Replace `YOUR_APP_URL_HERE` with the live Shiny app URL |
| Member org list | `_site_data.yml` | Edit the `member_orgs` list (note: org pills removed from homepage by default — re-add if desired) |

### What you DON'T need to touch:
- `styles.css` — only if you want design changes
- `_quarto.yml` — only if you add/remove pages or change nav structure
- `_includes.html` — never, unless adding global scripts

### Annual tasks (January):
1. Copy the KOL_DATA array in `events.qmd`, clear old entries, fill new speakers as confirmed
2. Add previous year's KOL talks to the archive table in `events.qmd`
3. Review leadership cards in `about.qmd` for any role/affiliation changes

