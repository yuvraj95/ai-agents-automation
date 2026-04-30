# Automation — PM Task Reminders and Visibility on Slack

## Problem

As a PM managing multiple concurrent releases and sprints, critical tasks — pending approvals, overdue tickets, upcoming deadlines — were easy to lose track of across Jira. Visibility of blockers and at-risk items was reactive rather than proactive.

---

## Automation Overview

A set of scheduled Zapier workflows that query Jira daily and weekly, identify tasks requiring PM attention, and post structured summary digests to Slack — giving proactive visibility without requiring manual Jira triage.

---

## Automations in This Set

### 1. Daily PM Standup Digest (Weekdays, 9:00 AM)

**Trigger:** Scheduled daily  
**Actions:**
1. Query Jira for tickets assigned to PM that are:
   - Due within 48 hours
   - In "In Progress" with no update in last 2 days (stale)
   - Blocked (status = "Blocked")
2. Format into a structured digest
3. Post to PM's personal Slack DM or `#pm-daily` channel:

```
Good morning. Here's your Jira digest for today:

Due within 48 hours:
- [Ticket Title] — [Link] — Due: [Date]

Stale (no update in 2 days):
- [Ticket Title] — [Link] — Last updated: [Date]

Blocked:
- [Ticket Title] — [Link] — Blocked reason: [Comment]
```

---

### 2. Weekly Sprint Health Summary (Mondays, 9:00 AM)

**Trigger:** Scheduled weekly  
**Actions:**
1. Query Jira for current active sprint
2. Pull: total tickets, completed, in progress, not started, blocked
3. Calculate completion percentage
4. Post to `#sprint-updates` Slack channel:

```
Sprint Health — Week of [Date]

Total tickets: X | Completed: X | In Progress: X | Not Started: X | Blocked: X
Completion: XX%

Attention needed:
- [List of blocked or at-risk tickets]
```

---

### 3. Upcoming Release Deadline Reminder (3 days before release date)

**Trigger:** Jira ticket with label `release-global` has a due date 3 days away  
**Actions:**
1. Pull all open sub-tasks under the release ticket
2. Identify incomplete sub-tasks
3. Post to `#releases` Slack channel tagging relevant owners:

```
Reminder: [Release Name] is due in 3 days.

Outstanding tasks:
- [Task Title] — Assigned to: @name — Status: [Status]
- [Task Title] — Assigned to: @name — Status: [Status]
```

---

## Impact

- Improved PM visibility over sprint health and at-risk items without manual Jira checking
- Reduced instances of missed deadlines and unaddressed blockers
- Kept cross-functional teams aligned on release readiness proactively
- Improved overall operational efficiency and PM responsiveness
