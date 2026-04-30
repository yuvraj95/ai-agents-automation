# Automation — Monthly Release Newsletter

## Problem

Every month, a release newsletter needed to go out to customers summarizing what shipped. The PM was manually pulling release notes from Jira, cross-referencing Slack product update posts, formatting them into readable customer-facing copy, and preparing a draft in HubSpot — a process that took several hours each month.

---

## Automation Overview

A Zapier workflow that runs monthly, pulls product update data from Jira and Slack, passes it to Claude to generate a customer-facing newsletter draft, and creates a ready-to-review draft in HubSpot — requiring only a final review and send from the PM.

---

## Trigger

Scheduled Zapier trigger — runs on the first working day of each month

---

## Actions

1. **Fetch from Jira:** Pull all tickets with label `global-release` that were closed in the previous month — extract titles, descriptions, and release notes fields

2. **Fetch from Slack:** Pull messages from `#product-updates` channel from the previous month — captures any additional context or announcements posted by the team

3. **Pass to Claude (Anthropic API via Zapier):**
   - Input: Structured list of Jira release items and Slack product updates
   - Prompt: Generate a customer-facing monthly release newsletter in a friendly, professional tone. Summarize each feature in one to two sentences from the customer's perspective. Group by product area. Include a short intro and closing line.
   - Output: Formatted newsletter draft

4. **Create draft in HubSpot:**
   - Uses HubSpot customer segment data to personalize the draft (customer name field tokens)
   - Creates email draft in HubSpot Marketing with subject line: "What's new at Sprinto — [Month Year]"
   - Draft is ready for PM review before sending

---

## Impact

- Reduced monthly newsletter preparation time from several hours to under 30 minutes (review and send only)
- Improved consistency of customer-facing release communication
- Ensured no releases were missed in monthly summaries
- Draft quality from Claude was high enough to require minimal edits in most months
