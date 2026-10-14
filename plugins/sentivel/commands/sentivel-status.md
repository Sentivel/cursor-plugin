---
name: sentivel-status
description: Show what is down, open incidents and who is on call.
---

# Sentivel status

1. Call `sentivel_whoami`.
2. Call `sentivel_list_monitors` and list any monitor that is not up.
3. Call `sentivel_list_incidents` and list open incidents with their latest update.
4. Call `sentivel_list_schedules`, then `sentivel_get_schedule` for each one, and say who is on call now.

Keep the answer short. If everything is up and nothing is open, say that in one line.
