# How to Add a History Reflection (for the site manager)

When a contributor sends you a finished piece, here is how to add it.

## Steps

1. Copy the template file `history/pieces/_TEMPLATE.qmd`.
2. Rename the copy using the date and a short title:
   `2026-Q2-randomization-early-years.qmd`
   (Format: year-quarter-short-title.qmd, all lowercase, dashes not spaces.)
3. Open the copy and fill in the four fields at the top from what they sent:
   - `title:` their title, in quotes
   - `author:` their name and affiliation, in quotes
   - `date:` convert their date to YYYY-MM-DD format (e.g. "March 2026" becomes 2026-03-15; any day in the month is fine)
   - `description:` their one-sentence summary, in quotes
4. Paste the body of their reflection below the top section, replacing the
   sample text. Delete the instruction comment block.
5. Save, then commit and push in GitHub Desktop (or upload via the browser).

The piece appears automatically at the top of the History & Achievements page.
No other file needs to be touched.

## Date format reminder

The `date:` field must be YYYY-MM-DD or the piece will not sort correctly:
  - "January 2026"  becomes  2026-01-15
  - "Q2 2026"       becomes  2026-04-15
  - "Fall 2026"     becomes  2026-10-15
The day does not matter, only the year and month, so the 15th is a safe default.
