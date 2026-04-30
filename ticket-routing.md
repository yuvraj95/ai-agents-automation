# Automation — Intelligent Ticket Auto-Routing

## Problem

New Jira tickets created by CS, engineering, or stakeholders were landing in a general backlog without being routed to the correct product pod. PMs were spending time manually triaging and assigning tickets — a low-value task that also introduced delays in tickets reaching the right team.

---

## Automation Overview

A Zapier workflow that detects newly created Jira tickets, reads the product area label or component field, and automatically routes the ticket to the correct pod by assigning it to the right PM and notifying the pod's Slack channel.

---

## Trigger

New ticket created in Jira project with status "Open" and no assignee

---

## Routing Logic

| Product Area (Label/Component) | Assigned Pod | Slack Channel Notified |
|---|---|---|
| `integrations` | Integrations Pod PM | #pod-integrations |
| `compliance-automation` | Compliance Pod PM | #pod-compliance |
| `reporting` | Reporting Pod PM | #pod-reporting |
| `onboarding` | Growth Pod PM | #pod-growth |
| `billing` | Platform Pod PM | #pod-platform |
| No label / unknown | General PM backlog | #pm-triage |

---

## Actions

1. Read ticket's component or label field
2. Match against routing table
3. Assign ticket to correct pod PM in Jira
4. Post notification to pod Slack channel:
   > "New ticket assigned to your pod: [Ticket Title] — [Jira Link]. Priority: [Priority]. Created by: [Reporter]."
5. If no label match, route to triage channel with a flag for manual review

---

## Impact

- Eliminated manual ticket triage by PM
- Reduced average time from ticket creation to pod assignment
- Improved visibility across pods — each team sees new tickets immediately in their Slack channel
- Freed PM time from low-value sorting tasks to focus on higher-value product work
