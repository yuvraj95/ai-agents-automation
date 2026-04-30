# Automation — Jira Pre-Dev Release Workflow

## Problem

Every new feature going into development required a standardized set of Jira tickets, labels, and structure to be created before the sprint began — covering release type (global vs pilot), release notes, backlog grooming tasks, and stakeholder sign-off checkpoints.

This was being done manually by the PM for every release cycle, leading to inconsistencies and missed steps.

---

## Automation Overview

A Zapier workflow that automatically scaffolds the full pre-development Jira structure when a new release is initiated — tailored to whether it is a **global release** or a **pilot release**.

---

## Trigger

A specific Jira ticket is created with a defined label: `release-global` or `release-pilot`

---

## Actions (Global Release Flow)

1. Create sub-tasks automatically:
   - Release notes ticket (assigned to PM)
   - Backlog grooming ticket (assigned to PM)
   - Stakeholder sign-off ticket (assigned to relevant stakeholder)
   - QA ticket (assigned to QA lead)
   - Enablement playbook ticket (assigned to CS lead)
2. Apply standard labels and epic links
3. Set due dates relative to release date (pulled from parent ticket)
4. Post notification to designated Slack channel: `#releases` with ticket summary and links

---

## Actions (Pilot Release Flow)

1. Create sub-tasks:
   - Pilot customer selection ticket (assigned to PM)
   - Success criteria definition ticket (assigned to PM)
   - Pilot monitoring ticket (assigned to PM)
   - Feedback collection ticket (assigned to CS)
2. Apply `pilot` label and link to pilot epic
3. Post notification to `#pilot-releases` Slack channel

---

## Impact

- Eliminated manual ticket creation for every release cycle
- Standardized pre-dev structure across all releases — no missed steps
- Reduced PM setup time per release from ~30 minutes to zero
- Improved release readiness and cross-team visibility from day one of each cycle
