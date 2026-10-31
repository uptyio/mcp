---
name: destructive-actions
description: Resolve the exact target and follow Upty's preparation/confirmation workflow for resource deletion and other destructive monitoring changes. Use when a Upty operation can delete data or remove monitoring coverage.
---

# Destructive Upty changes

Resolve the exact resource with read tools and explain the concrete consequence of the requested operation. Similar names are not sufficient to identify a target: clarify ambiguity before changing anything.

Use `prepare_deletion` for a monitor, maintenance window, status page or incident, followed by `confirm_deletion` for the final operation. Preparations expire after five minutes and are single-use. Inspect its returned target and consequence; obtain any confirmation required by the client or applicable user authorization rules before the final operation. Send the preparation token and exact confirmation name only for that same approved target and operation. A token returned by the server is not itself human approval; do not describe it as proof of user consent or reuse it for a different target.

Respect authorization already given for a concrete, unchanged action. Do not introduce extra approval loops merely because this skill exists. If the target or consequence differs from what the user authorized, explain the change and clarify it.

Verify the result with the relevant read tool and report what was removed or changed. On a permission or plan error, stop that operation and explain the restriction; do not use another endpoint, workspace or credential to bypass it.
