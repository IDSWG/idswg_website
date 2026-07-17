# Go-Live Checklist — DahShu IDSWG Website

Complete these steps before making the site public.

## 1. GitHub Setup (Required for deployment)
- [ ] Create a GitHub account if you don't have one (github.com)
- [ ] Create a new repository named `idswg_website` (or similar)
- [ ] Upload/push the project folder contents to the repository
- [ ] Go to Settings → Pages → Source: **Deploy from branch** → branch: **gh-pages**
- [ ] Update `site-url` in `_quarto.yml` from `https://idswg.github.io` to your actual URL (e.g. `https://yourusername.github.io/idswg_website`)
- [ ] Push to `main` branch — GitHub Actions will auto-deploy via `.github/workflows/publish.yml`

## 1b. Set Your Mailing List URL (Required)
Search for `MAILING_LIST_URL_HERE` in these files and replace with your actual signup link:
- `index.qmd`
- `join.qmd`
- `about.qmd`
- `_quarto.yml` (footer)

This should be whatever signup page you use for the IDSWG mailing list (e.g. a Substack, Mailchimp, Google Form, or WildApricot link — whichever the group currently uses).

## 2. Content Verification (Required)
- [ ] Confirm all leadership names, titles, affiliations, and emails are accurate in `about.qmd`
- [ ] Confirm all leadership emails are accurate in `join.qmd` contact table  
- [ ] Verify the Zoom link in `events.qmd` is still active
- [ ] Verify DahShu mailing list URL (`dahshu.wildapricot.org`) still works
- [ ] Verify all 4 publication DOI links resolve correctly
- [ ] Confirm the KOL 2025 schedule in `events.qmd` is accurate (Oct–Dec topics)

## 3. Links to Verify
- [ ] LinkedIn group link: https://www.linkedin.com/groups/18890018/
- [ ] Randomization WG: https://www.randomizationwg.com
- [ ] DahShu: https://dahshu.wildapricot.org
- [ ] All external regulatory links (FDA, EMA, ICH) in `regulatory.qmd`

## 4. Information to Update
- [ ] `_quarto.yml` → `site-url`: replace placeholder with actual deployed URL
- [ ] `robots.txt` → `Sitemap:` line: replace placeholder URL with actual URL
- [ ] `_includes.html` → JSON-LD `"url"` field: update to actual URL
- [ ] `CNAME`: if using a custom domain (e.g. `idswg.org`), add it here; otherwise leave blank

## 5. Optional Before Launch
- [ ] Register a custom domain (e.g. via Namecheap, Google Domains) and configure CNAME
- [ ] Enable Plausible Analytics — uncomment the analytics section in `_quarto.yml` and add your domain
- [ ] Send preview link to leadership team for review before announcing publicly

## 6. Announce
- [ ] Post on LinkedIn group: https://www.linkedin.com/groups/18890018/
- [ ] Send to DahShu mailing list
- [ ] Notify sub-team leaders to share with their members

## Common Questions

**Q: Do I need to know coding to maintain the site?**  
A: No. Most updates (news posts, publications, KOL schedule) involve editing plain text. The README has a step-by-step cheat sheet.

**Q: What if something breaks after I push a change?**  
A: The GitHub Actions log (under Actions tab in your repo) will show what went wrong. The previous working version is always in the git history — you can revert by undoing your last commit.

**Q: How do I add a co-maintainer?**  
A: Add them as a Collaborator on the GitHub repository (Settings → Collaborators). They'll be able to push changes that trigger auto-deployment.
