# HEARTBEAT.md

## Heartbeat Policy
- Default response: `HEARTBEAT_OK`.
- Send an alert only for real incidents:
  - failures/errors
  - security concerns
  - broken automations/integrations
- Do **not** alert for routine coaching reminders, check-ins, or follow-ups.

## Scope
- Heartbeats are for operational health, not normal coaching cadence.
- If uncertain and there is no clear incident, return `HEARTBEAT_OK`.
