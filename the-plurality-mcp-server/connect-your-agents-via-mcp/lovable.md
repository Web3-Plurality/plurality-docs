---
description: 'Last updated: April, 2026'
---

# Lovable

> **TL;DR** Lovable's paid plans support MCP directly in the builder. Connect once and your memory becomes a live data source for whatever you build.

#### Prerequisites

* A paid Lovable plan
* A Lovable project open

#### Setup

1. Open your Lovable project.
2. Navigate to **Settings → Connectors → Personal Connectors → New MCP Servers**.
3. Click **Connect MCP** and paste: `https://app.plurality.network/mcp`
4. Authenticate via OAuth in the browser window that opens.
5. The connector appears in your project's available connectors.

#### Use it

Once connected, reference your Plurality memory directly in Lovable prompts. For example:

> _"Build a dashboard that shows my last 5 saved notes from my Plurality memory."_

Your memory buckets, documents, and notes act as live data for the apps you generate.

#### Verify

In a Lovable prompt, ask the builder to read from Plurality. If it returns content from your buckets, the connection is working.

#### Troubleshoot

**MCP option missing in Connectors.** You're on a Free plan. MCP requires a paid plan.

**OAuth completes but Lovable doesn't see the tools.** Refresh the project page after authentication.
