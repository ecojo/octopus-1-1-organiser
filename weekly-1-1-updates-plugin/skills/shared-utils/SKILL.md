---
name: shared-utils
description: Internal utility functions for the Weekly 1:1 Updates plugin. This skill is not meant to be triggered directly—it provides shared helper functions and reference materials used by the setup wizard, employee update, manager updates, and scaffolder skills.
---

# Shared Utilities

Internal utilities and helper functions for the Weekly 1:1 Updates plugin.

## Overview

This skill is not user-facing—it provides shared functions that the other skills reference:

- JIRA query builders (constructing issue queries by person, board, status)
- Confluence page operations (creating, updating, setting permissions)
- Email parsing (extracting feedback from Outlook messages)
- Date formatting and quarter/half-year calculations
- Configuration validation (checking that setup is complete)

## Shared Functions

### JIRA Helpers

```
get_issues_for_user(jira_boards, assignee_email, date_range)
  → Returns list of issues assigned to user in past week

get_blockers(jira_boards, assignee_email)
  → Returns high-priority/blocker issues

build_jira_summary(issues)
  → Formats JIRA issues into readable summary (accomplishments, in-progress, blockers)
```

### Confluence Helpers

```
create_1_1_page(space_key, employee_name, manager_name, date, content)
  → Creates or updates 1:1 page with given content and permissions

get_employee_1_1_folder(space_key, employee_name)
  → Gets/creates employee subfolder structure

set_page_permissions(page_id, manager_email, employee_email)
  → Restricts page to manager + employee only

get_page_content(space_key, page_title)
  → Reads existing page content (for context)

create_year_folder(space_key, employee_name, year)
  → Creates year folder if it doesn't exist
```

### Email Helpers

```
find_manager_feedback_email(folder_name_or_pattern, employee_name)
  → Searches Outlook for feedback email matching pattern

extract_feedback_text(email_message)
  → Parses email body for key feedback points

get_latest_feedback_date(folder_name_or_pattern, employee_name)
  → Returns date of latest feedback email
```

### Date/Config Helpers

```
calculate_next_quarter()
  → Returns (start_date, end_date) for next quarter

calculate_next_half_year()
  → Returns (start_date, end_date) for next half-year

get_weekly_dates_in_period(start_date, end_date)
  → Returns list of Wednesdays (or configured day) in period

format_date_for_page_name(date, format_pattern)
  → Formats date according to configured pattern (e.g., "07 Jan 2026")

validate_setup_complete()
  → Checks that plugin config is valid and required tools are connected

load_team_config()
  → Reads saved config from plugin storage
```

### Synthesis Helpers

```
synthesize_1_1_summary(jira_summary, feedback_text, confluence_context)
  → Combines JIRA, feedback, and Confluence notes into structured summary

format_for_confluence(summary_dict)
  → Converts summary dictionary into Confluence page format with headers, lists, etc.
```

## Configuration Storage

The plugin stores team configuration (set during setup) in a shared location that all skills access:

```json
{
  "team_name": "Engineering",
  "timezone": "America/Los_Angeles",
  "manager_email": "marc.garcia@company.com",
  "manager_name": "Marc Garcia",
  "confluence_space_key": "WEEKLY",
  "confluence_date_format": "DD MMM YYYY",
  "employees": {
    "david.hoffmann@company.com": {
      "name": "David Hoffmann",
      "jira_boards": ["BCR", "BonusFinder Dev"],
      "feedback_email_pattern": "David 1:1 Weekly Feedback",
      "one_on_one_day": "Wednesday",
      "one_on_one_time": "09:00"
    },
    ...
  },
  "scaffold_frequency": "quarterly",  // or "half_yearly"
  "scaffold_day_of_month": 1,
  "scaffold_time": "00:00"
}
```

## Error Handling

All helpers include error handling for common issues:
- **JIRA board not found** → Warning logged, function returns empty list
- **Confluence space doesn't exist** → Offers to create it
- **Email not found** → Returns null, parent skill handles gracefully
- **Permission denied** → Reports which scopes are missing

## Usage in Other Skills

Each skill imports relevant helpers:

- **Setup Wizard** → Config validation, Confluence creation
- **Employee Update** → JIRA query, email fetch, Confluence read/write, synthesis
- **Manager Updates** → JIRA query (per employee), email fetch (per employee), Confluence creation (per employee)
- **Scaffolder** → Date calculation, year folder creation, page creation

---

This skill is internal to the plugin. You don't interact with it directly, but it powers the other skills.
