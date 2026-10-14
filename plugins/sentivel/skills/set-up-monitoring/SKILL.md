---
name: set-up-monitoring
description: Add Sentivel monitors, components and a status page for the project open in Cursor. Use when the user wants uptime monitoring or a status page for their app.
---

# Set up monitoring

## When to use

- The user asks to monitor their app, API or site.
- The user wants a public status page.
- A new service or endpoint has shipped and has no monitor.

## Steps

1. Call `sentivel_whoami` to confirm the workspace and role.
2. Read the project to find what is public: deploy config (`vercel.json`, `fly.toml`, `railway.json`, Dockerfiles), route files, health endpoints and environment examples. Note each production URL and any `/health` or `/status` route.
3. Call `sentivel_list_monitors` and `sentivel_list_components` to see what exists.
4. Show the user a short plan before creating anything: one component per thing customers notice (Website, API, Dashboard) and the monitors behind each one.
5. After the user agrees, create the components with `sentivel_create_component`, then the monitors:
   - `sentivel_create_http_monitor` for URLs. Point it at a health route when there is one.
   - `sentivel_create_tcp_monitor` for databases, mail servers or other ports.
   - `sentivel_create_heartbeat` for cron jobs and workers. Add the ping to the job's code and show the user the diff.
6. Ask which third-party services the app depends on (hosting, payments, auth, email). Use `sentivel_list_providers` and `sentivel_list_provider_components` to find them, then `sentivel_link_dependency` to link each one to the component that uses it. When a linked provider has an outage, the component's status changes with it.
7. If the user wants a status page, create it with `sentivel_create_status_page` and add the components.
8. Finish with a list of what you created and the status page URL.
