---
name: create-monitor
description: Create and verify a Upty monitor for an explicitly requested service. Use for website, API, network, certificate, domain, DNSSEC, external status-page, heartbeat or log monitoring within the connected workspace.
---

# Create a Upty monitor

Use `list_monitors` to check existing resources, `list_regions` for available probes, `create_monitor` to create, and `get_monitor` to verify the result.

Identify the requested target and monitor type. Use the available tools to inspect supported regions and existing monitors; avoid creating a duplicate when the requested monitor already exists. Use the connected workspace's plan limits and available input schema rather than inventing intervals or probe regions.

For DNSSEC use `data.type="dnssec"`, the signed domain in `target`, and `warn_days` for signature warnings (default 7). A valid chain nearing signature expiry is Degraded, not Down. An unsigned zone is not a healthy DNSSEC result.

For an upstream status page use `data.type="external_status_page"`, its public page/feed URL in `target` and optional `external_status_page` settings (`provider`, `component_names`, `component_group`). Auto and an empty scope watch the whole page. Preserve the complete intended provider and component/group scope when replacing this nested settings object. External Status Page requires Pro or Business; a Full access connection does not bypass the plan. MCP/API access is separate from a monitor type being available in the Free dashboard.

Proceed with ordinary settings that follow the user's request. Clarify only choices that materially change the target, failure criteria or alert recipients. Creating a monitor does not by itself authorize creating new notification channels or sending a test alert.

After creation, retrieve the resulting monitor and report its name, type, target, interval and current state. A successful create response confirms configuration, not that the first check has passed: say “pending” until there is an actual check result. Do not poll indefinitely; if checks have not arrived, report the current state and latest observation.

Never print a heartbeat's secret URL, ingestion token or stored request credentials in a shared report. Read-only connections cannot create monitors; explain the access restriction without trying another route around it.
