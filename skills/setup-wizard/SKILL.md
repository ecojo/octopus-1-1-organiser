---
name: setup-wizard
description: Configure the Weekly 1:1 Updates plugin for your team. Use this when a manager wants to set up the plugin for their team—it guides you through connecting required tools (JIRA, Confluence, Outlook/Email, Slack, Teams), defining team members, mapping JIRA boards, setting up email feedback patterns, and creating the Confluence folder structure with permissions. Run this first before using employee or manager update skills.
---

# Setup Wizard for Weekly 1:1 Updates

This skill guides you through configuring the plugin for your team and optionally creates the Confluence infrastructure (folder structure, pages, permissions) needed for weekly 1:1 updates.

## What You'll Configure

1. **Team basics** — Team name, manager email, timezone
2. **Team members** — Employee names, emails, JIRA board assignments
3. **Email feedback setup** — How your manager sends weekly feedback (folder-based or direct emails)
4. **Confluence space** — Create or use existing space for 1:1 pages
5. **1:1 meeting times** — Auto-discover from Outlook or manually enter each employee's meeting time
6. **Permissions** — Set manager + employee view access

## Required Connectors

Before running this wizard, ensure you have these connectors enabled in your workspace:

- **JIRA** (required) — to pull work updates from your boards
- **Confluence** (required) — to create and read 1:1 pages
- **Outlook/Email** (required) — to read manager feedback emails
- **Slack** (optional but recommended) — if your team uses Slack for feedback
- **Teams** (optional but recommended) — if your team uses Teams for feedback/notes

If any are missing, go to your workspace connectors settings and enable them before continuing.

## Interactive Configuration Flow

When you run this skill, I will ask you the following questions in order. Answer each one:

### Team Setup
- **Team name** — What should we call this team? (e.g., "Engineering", "Product")
- **Your email** — Your email address (you're the manager)
- **Timezone** — Your timezone (e.g., America/Los_Angeles) — used for scheduling

### Team Members
- **How many direct reports?** — Tell me how many people report to you
- **For each employee:**
  - Name
  - Email
  - Which JIRA boards do they work on? (can be multiple)
  - Separate JIRA board config for each employee? (important if different people track different boards)

### Manager Feedback Email Setup
- **How is feedback organized?**
  - Option A: Direct emails to you with subject pattern like "[Name] 1:1 Weekly Feedback"
  - Option B: All feedback emails in a shared folder called "Weekly Feedback" or similar
- **Email folder/subject pattern** — Provide the folder name or subject pattern so we can find emails

### Confluence Space
- **Does a Confluence space exist for your team?**
  - If yes: What's the space key or name?
  - If no: I can create one. What should we call it? (e.g., "Weekly Feedback", "Team Updates")

### 1:1 Meeting Times
I can discover your 1:1 meeting times two ways:

**Option A: Auto-discover from Outlook**
- I'll search your Outlook calendar for meetings marked "1:1" and extract the day/time for each employee
- This is fastest if your 1:1 meetings are already scheduled

**Option B: Manual entry**
- You tell me when each employee's 1:1 is (e.g., "David Hoffmann - Wednesday 9am", "Sarah Chen - Monday 2pm")
- This is more flexible if meetings aren't yet scheduled or have irregular timing

Choose which approach works for your team.

### Permissions
- Confirm that 1:1 pages should be visible to manager + that specific employee only (not the whole team)

## What Happens After Configuration

I will:

1. **Validate** all connectors are accessible (try connecting to JIRA, Confluence, Outlook)
2. **Ask for confirmation** — show you the full config before creating anything
3. **Create Confluence infrastructure** (if needed):
   - Main folder: "Weekly Feedback"
   - Employee subfolders: "{Full Name} 1:1s" (e.g., "David Hoffmann 1:1s")
   - Year folders inside each: "2026", "2027", etc.
   - Placeholder 1:1 pages: "{Full Name} - Manager 1:1 - [Date]" for upcoming weeks
   - Permissions: Manager + employee only
4. **Save your configuration** to a config file for future use by the scheduled tasks and update skills

## Important Notes

- **Config is reusable** — Once saved, the employee and manager update skills will use this config automatically
- **Edit config anytime** — If team members change, JIRA boards change, or meeting times shift, you can re-run this wizard to update
- **Confluence creation is optional** — If you already have a space set up, you can skip creating new infrastructure
- **Timezones matter** — Make sure your timezone is correct so scheduled tasks run at the right time

## Next Steps

After setup:

- **For employees**: They run the "Employee 1:1 Prep" skill each week (or it's scheduled to run automatically before their 1:1)
- **For you (manager)**: You run the "Manager Pulls All Reports" skill to get a consolidated view of all team updates, or it's scheduled to run before each employee's meeting
- **Weekly scaffolding**: The plugin automatically pre-creates placeholder 1:1 pages for next quarter on a monthly schedule

---

## Running the Setup Wizard

I'm ready to guide you through this. Just tell me you want to set up the plugin, and I'll ask the questions above step-by-step. Once you answer them all, I'll validate, create infrastructure, and save your config.

Ready to get started?
