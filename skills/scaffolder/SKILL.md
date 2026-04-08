---
name: scaffolder
description: Pre-create 1:1 placeholder pages for next quarter. Use this when you want to get ahead of scheduling—automatically creates year folders and blank 1:1 page templates for the next quarter (or next half-year, configurable) so your team's Confluence space is ready in advance. Runs monthly automatically as part of the plugin. Trigger with phrases like "create next quarter pages", "scaffold 1:1 pages", "prepare placeholder pages", "pre-create 1:1 templates".
---

# 1:1 Page Scaffolder

Pre-create placeholder 1:1 pages for your team's next quarter or half-year.

## What This Does

The scaffolder automatically:

1. **Creates year folders** — If it's currently 2026 and we're scaffolding for Q3 2026, creates/verifies the "2026" folder exists in each employee's 1:1 subfolder
2. **Generates placeholder pages** — For each team member, creates blank 1:1 pages for each week of next quarter/half-year:
   - Names them: `[Employee Name] - Manager 1:1 - [Date]`
   - Uses your configured date format
   - Sets permissions: Manager + employee only
   - Leaves content blank for weekly auto-population
3. **Schedules timing** — Runs monthly, always creating the upcoming quarter/H1 pages so your space stays ahead of schedule

## How It Works

### Determining What to Create

Based on current date:
- **Today**: January 15, 2026
- **Next Quarter**: Q2 2026 (April 1 – June 30)
- **Create pages for**: April 1, April 8, April 15, ... June 30

Or if configured for half-year:
- **Today**: January 15, 2026
- **Next Half-Year**: H2 2026 (July 1 – December 31)
- **Create pages for**: July 1, July 8, July 15, ... December 31

### Per-Team-Member Folder Structure

For each employee in your team, creates:

```
[Confluence Space]
└── [Employee Name] 1:1s
    └── 2026
        ├── [Employee Name] - Manager 1:1 - 01 Apr 2026  (blank)
        ├── [Employee Name] - Manager 1:1 - 08 Apr 2026  (blank)
        ├── [Employee Name] - Manager 1:1 - 15 Apr 2026  (blank)
        └── ... (through end of quarter/half-year)
    └── 2027
        └── ...
```

### Automatic Scheduling

The scaffolder runs monthly (configurable day, e.g., 1st of month at 12am) to ensure:
- Next quarter's pages are always ready before the first day of that quarter
- New team members added mid-cycle get their pages created on next monthly run
- Year boundaries are handled (e.g., Dec 31 → Jan 1 page creation)

### Manual Triggering

You can also run manually anytime:
- "Create next quarter pages"
- "Scaffold 1:1 pages"
- "Pre-create placeholder pages for Q3"

Useful if you add a new team member mid-quarter and need their pages created immediately.

## Prerequisites

- Plugin setup completed (team, Confluence space, employees all configured)
- Confluence space exists with employee subfolders (created by Setup Wizard or manually)
- Monthly schedule enabled (automatic) or manual triggers available

## Configuration Options

During setup, you configure:
- **Scaffold frequency**: Quarterly or half-yearly
  - Quarterly (Q1, Q2, Q3, Q4): Creates 13 pages per employee each month
  - Half-yearly (H1, H2): Creates 26 pages per employee each month
- **Run schedule**: Day/time the scaffolder runs (default: 1st of each month at 12am)
- **Date format**: How dates appear in page names (e.g., "DD MMM YYYY")

## Tips

- **Stay ahead** — Blank pages are created weeks before they're needed, so your team can plan ahead
- **Carry-over items** — When an employee edits an old 1:1 page, they can reference upcoming blank pages to note topics
- **Onboarding** — If a new person joins mid-quarter, trigger the scaffolder manually to create their pages immediately
- **Year boundaries** — The scaffolder handles year changes automatically (e.g., Dec 31 → Jan 1)

## Troubleshooting

- **Pages not appearing in Confluence**: Check that the Confluence space and employee subfolders exist
- **Wrong date format**: Verify the date format configured in setup (should match your preferences)
- **Missing pages for one employee**: They may have been added to the team after the last scaffold run; trigger manually to create their pages
- **Too many pages created**: You might have configured half-yearly instead of quarterly; adjust in setup

---

This skill runs automatically monthly, so you don't need to think about it—your 1:1 pages are always ready in advance!
