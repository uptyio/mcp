# Upty MCP plugin

Connect your monitoring workspace to a compatible AI assistant through [Upty](https://upty.io).

This repository contains the **public Claude Code plugin**, connection configuration and workflow skills. The hosted MCP server and Upty backend are maintained separately. No server code, credentials or customer data are included here.

## Claude Code

```sh
claude plugin marketplace add uptyio/mcp
claude plugin install upty@upty
```

Restart Claude Code if needed, open `/mcp`, select **upty**, and authenticate. Your browser opens Upty: sign in, choose your workspace and **Read-only** or **Full access**, then approve. The plugin contains no API token.

You can also connect directly, without the plugin:

```sh
claude mcp add --transport http upty https://mcp.upty.io/mcp
```

## Other clients

MCP endpoint: **`https://mcp.upty.io/mcp`**.

Add that address as a remote MCP server in a client that supports **Streamable HTTP with OAuth**. Follow its sign-in flow and approve the workspace and access level in Upty. Availability and setup labels depend on the client and subscription; consult its current documentation. A remote MCP endpoint alone does not mean a client or marketplace integration has been certified.

Examples include an MCP custom connector in compatible web assistants, or a remote MCP entry in a desktop/CLI client. This plugin itself is a Claude Code package; it is not an OpenAI or Anthropic marketplace listing.

## What to ask

- “Which monitors are down or degraded in this workspace?”
- “Show the response-time and uptime history for the checkout API.”
- “Create an HTTPS monitor for my website using the regions and interval my plan allows.”
- “Pause the maintenance check until I resume it.”
- “List the maintenance windows and public status pages.”

The tool list returned by your connection is authoritative. Read-only connections cannot write; role and plan restrictions still apply to Full access. Some operations need whole-workspace permissions.

## Included skills

- **health-report** — summarize current monitoring health using read-only tools.
- **create-monitor** — resolve monitor settings, create the monitor and verify its resulting state.
- **destructive-actions** — identify the exact target and use the server's confirmation workflow for destructive changes.

The skills support the task you request. They do not grant additional permissions or authorize unrelated changes.

## Control access

Open **Upty → Integration & API → MCP · Connected apps** to inspect and disconnect applications. Revocation ends that connection's access. Removing a workspace membership or changing its permissions also changes what the app may do. Actions are attributed to the user and connected application.

Do not paste access tokens, heartbeat URLs, host tokens, passwords or channel credentials into an issue. Send only a redacted error and the affected tool name. See the [connection guide](https://upty.io/docs/mcp).

## License

[MIT](LICENSE).
