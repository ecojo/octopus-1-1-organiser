---
name: employee-update
description: Generate your weekly 1:1 prep by pulling JIRA updates, Confluence notes, and manager feedback. Use this when you want to prepare for your 1:1 meeting—it automatically gathers your recent work from JIRA boards (as configured in setup), reads any manager feedback from email, pulls notes from your Confluence 1:1 page, and generates a summary you can review and edit. Works with the weekly schedule set up by the plugin setup wizard. Trigger with phrases like "prep my 1:1", "prepare for my 1:1", "generate my 1:1 update", "pull my updates for 1:1".
---

# Employee 1:1 Prep

Generate your weekly 1:1 update by pulling your work updates, manager feedback, and personal notes.

## What This Does

Each week, this skill:

1. **Pulls from JIRA** — Gathers issues/tickets you've worked on this week from your configured boards
2. **Reads manager feedback** — Retrieves the latest feedback email from your manager (e.g., "David 1:1 Weekly Feedback")
3. **Checks Confluence notes** — Reads any notes from your previous 1:1 page to carry forward context
4. **Generates 1:1 summary** — Synthesizes all of this into a structured summary with:
   - Key accomplishments this week
   - Current work in progress
   - Blockers or concerns
   - Manager feedback/alignment from their email
   - Suggested talking points for your 1:1
5. **Creates/updates Confluence page** — Writes the summary to your weekly 1:1 page in Confluence (you can edit it before your meeting)

## How It Works

### Pulling JIRA Updates

The skill queries your configured JIRA boards for:
- Issues you've worked on (assigned to you, or you've commented on)
- Tickets closed/completed this week
- Work in progress (sprints, backlogs)
- Any blockers or high-priority items

It extracts issue titles, descriptions, status, and your comments to build a narrative of your week's work.

### Reading Manager Feedback

The skill searches your email for messages from your manager that match the feedback email pattern configured during setup. For example:
- Subject pattern: "[Your Name] 1:1 Weekly Feedback" (direct emails)
- Folder: "Weekly Feedback" containing all team member feedback

It pulls the latest message and extracts:
- Feedback on your performance/work
- Alignment/priority expectations
- Any action items for you
- Anything else your manager flagged for discussion

### Confluence Context

The skill reads your current 1:1 page (or previous week's page) to check for:
- Any carry-over items from last week
- Open discussion topics
- Ongoing projects mentioned in past 1:1s

This gives you continuity and ensures nothing falls through the cracks.

### Generating the Summary

The skill synthesizes all three data sources into a structured summary organized as:

```
## Weekly Update for [Your Name] - [Date]

### Accomplishments This Week
- [Key completions from JIRA]
- [Highlights from manager feedback if any]

### Current Work in Progress
- [Active tickets/projects]

### Blockers or Concerns
- [Any blockers noted in JIRA or feedback]

### Manager Feedback & Alignment
[Content from manager feedback email summarized]

### Discussion Points for 1:1
- [Topics extracted from above]
- [Carryover items from last week]
- [Any questions or topics you flag]
```

### Creating/Updating the Page

The skill writes this summary to your Confluence 1:1 page. You receive the page URL and can:
- Review the generated content
- Edit anything before your meeting
- Add notes or personal context
- Share it with your manager if needed

The page is created with permissions set to manager + you only (private).

## Running the Skill

### Manual Trigger

Run this anytime you want to prep for your 1:1:
- "Prep my 1:1"
- "Generate my 1:1 update"
- "Pull my updates for my meeting"

### Automatic Schedule

If your manager set up the weekly schedule during plugin setup, this skill runs automatically:
- **Day/time**: The day and time of your configured 1:1 (e.g., Wednesday 9am)
- **Frequency**: Every week
- **Result**: The summary page is auto-generated and you get a notification to review it

You can still manually trigger it anytime if you want to regenerate before your actual meeting.

## Prerequisites

- Plugin setup has been completed (run the Setup Wizard first)
- Your JIRA boards are configured
- Your manager's feedback email pattern is configured
- Your Confluence 1:1 page exists (or the skill will create it)

## Tips

- **Edit before your meeting** — The generated summary is a starting point. Add your own context, insights, and questions before your 1:1
- **Keep it up-to-date** — If you complete major work mid-week, you can regenerate the summary closer to your 1:1
- **Reference past pages** — Your Confluence folder has all previous weeks' 1:1 pages for context
- **Ask your manager** — If something from your manager's feedback email doesn't make sense, bring it up in your 1:1

## Troubleshooting

- **Missing JIRA updates**: Make sure your JIRA boards are configured in the plugin setup and you're assigned to tickets
- **No manager feedback found**: Check that the email folder/subject pattern matches your actual feedback emails
- **Confluence page not created**: Verify you have write access to the Confluence space configured in setup

---

Ready to prep? Just ask "prep my 1:1" and I'll pull everything together for you.
