---
name: run-an-incident
description: Open, update and resolve a Sentivel incident, and look into the cause in the codebase. Use when something is down or a monitor is failing.
---

# Run an incident

## When to use

- A monitor is failing or the user reports an outage.
- The user asks what is on fire, who is on call or what changed.

## Steps

1. Call `sentivel_list_incidents` to check for an open incident before you create a new one.
2. Look at the affected monitors with `sentivel_get_monitor`, `sentivel_get_monitor_uptime` and `sentivel_get_monitor_response_times` to see when it started and how bad it is.
3. Check `sentivel_list_dependencies` for the affected component. If a linked provider is down, say so. That is often the cause.
4. If there is no open incident, draft one and show it to the user. Create it with `sentivel_create_incident` only after they agree.
5. Use `sentivel_get_schedule` to find who is on call and `sentivel_get_incident_escalation` to see who has been paged. `sentivel_acknowledge_incident` stops the escalation once someone is on it.
6. Look for the cause in the repo: recent commits (`git log --since`), changed config and the code behind the failing endpoint. Tell the user what you find. Don't deploy fixes on your own.
7. Draft each status page update for customers and post it with `sentivel_update_incident` after the user approves it.
8. When the monitors are green again, resolve the incident and use `sentivel_get_incident_timeline` to give the user a summary for the write-up.
