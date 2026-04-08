---
name: manager-updates
description: Pull all direct reports' 1:1 updates for manager review. Use this when a manager wants to see a consolidated view of their team's weekly updates before 1:1 meetings. The skill pulls each team member's JIRA updates, work progress, and manager feedback, then generates individual 1:1 prep pages for each report. Scheduled to run on each employee's 1:1 meeting day (morning) so you have everything ready before the meetings. Trigger with phrases like "pull all my reports' updates", "manager review", "team 1:1 updates", "get team updates for today's 1:1s".
---

# Manager Pulls All Reports' Updates

Consolidate all your direct reports' 1:1 prep in one action—pull JIRA, notes, and feedback for each team member.

## What This Does

For each of your direct reports, this skill:

1. **Pulls their JIRA updates** — Gathers work completed, in progress, and blockers from their assigned boards
2. **Reads their Confluence notes** — Checks their 1:1 page for any notes or carry-over items
3. **Synthesizes their week** — Generates a 1:1 prep page for each person with:
   - Their key accomplishments
   - Work in progress
   - Blockers or concerns
   - Topics for discussion
4. **Creates individual 1:1 pages** — Writes each team member's update to their dedicated Confluence 1:1 page

Then provides you with:
- A list of all team members' pages (links)
- A quick summary per person (key points at a glance)
- Timing so you're prepared before each 1:1

## How It Works

### Per-Employee Workflow

For each of your direct reports (as configured in setup):

1. **Query their JIRA boards** — Using their configured board list, pull issues:
   - Assigned to them (closed or in progress this week)
   - Recent activity/comments from them
   - Blockers or high-priority items
2. **Read their Confluence 1:1 page** — Check for any notes they've added or carry-over items from last week
3. **Generate their summary** — Synthesize into a structured update:
   - Accomplishments
   - Work in progress
   - Blockers/concerns
   - Topics for your 1:1
4. **Create/update their page** — Write the summary to their weekly 1:1 Confluence page

### Individual Pages

Each team member gets their own 1:1 page following your configured naming pattern:
- Location: `[Confluence Space] > [Employee Name] 1:1s > [Year] > [Employee Name] - Manager 1:1 - [Date]`
- Permissions: Manager + that employee only
- Content: Auto-generated summary + any employee edits

### Manager Summary

After pulling all reports, you get:
- **Quick summary** — Key points for each person (accomplishments, blockers, discussion topics)
- **Page links** — Direct links to each person's full 1:1 page in Confluence
- **At-a-glance view** — Helps you prepare talking points before back-to-back 1:1s

## Running the Skill

### Manual Trigger

Run anytime you want to pull your team's updates:
- "Pull all my reports' updates"
- "Manager review—get team updates"
- "Prepare for my 1:1s"

### Automatic Schedule

If setup created schedules for each 1:1:
- **Timing**: Morning of each team member's 1:1 (e.g., Monday 9am for one person, Wednesday 9am for another)
- **Frequency**: Automatically before each 1:1
- **Result**: Each person's page is generated, and you get a summary notification

This means you're always prepared for your 1:1s without having to manually check each person's work.

## Example Workflow

Imagine you have three direct reports:

- **David** — 1:1 on Monday 9am
- **Sarah** — 1:1 on Wednesday 9am
- **Jordan** — 1:1 on Friday 2pm

The plugin schedules:
- **Monday 9am** — Pulls David's updates, creates his Monday 1:1 page, sends you a summary
- **Wednesday 9am** — Pulls Sarah's updates, creates her Wednesday 1:1 page, sends you a summary
- **Friday 2pm** — Pulls Jordan's updates, creates his Friday 1:1 page, sends you a summary

You can also manually trigger anytime: "Pull all my reports' updates" to get everyone's status on demand.

## Prerequisites

- Plugin setup completed (run Setup Wizard first)
- Each team member's JIRA boards are configured
- Each team member has a Confluence 1:1 folder (created during setup or manually)
- Meeting times configured (auto-discovered from Outlook or manually entered)

## Tips for Managers

- **Review before 1:1** — Open each person's page 5-10 minutes before your meeting to refresh on key points
- **Identify patterns** — Across your team's pages, you might spot themes (e.g., shared blockers, capacity issues)
- **Add your own notes** — The pages are editable; you can add talking points, feedback, or decisions from your side
- **Follow up on blockers** — If multiple people flag similar blockers, this is a signal to address at team level
- **Track progress** — Previous weeks' pages show what was discussed and how people progressed

## Troubleshooting

- **Missing JIRA updates for a person**: Check their JIRA board configuration in plugin setup
- **Confluence pages not generating**: Verify the Confluence space exists and you have write access
- **Schedule not running**: Check that each employee's meeting time is correctly configured
- **Only some reports showing**: Confirm all team members are in the "direct reports" list in plugin setup

---

Ready to pull your team's updates? Manual trigger: "Pull all my reports' updates". Or if scheduled, check back before your first 1:1 of the week!
