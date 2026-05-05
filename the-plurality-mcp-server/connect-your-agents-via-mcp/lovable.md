---
description: 'Last updated: April, 2026'
---

# Lovable

> **TL;DR** Lovable's paid plans support MCP directly in the builder. Connect once and your memory becomes a live data source for whatever you build.

#### Prerequisites

* A paid Lovable plan
* A Lovable project open

#### Setup

1. Login to the Lovable website.
2. Open **Connectors** and go to **Chat connectors**.
3. Click **New MCP server**.
4. **Server name**: Enter a clear name for your server (for example, _AI Context Flow or Plurality MCP_).
5. **Server URL**: Enter the address where Lovable can reach your MCP server (https://app.plurality.network/mcp)
   1. **Authentication:**
      * **OAuth (default):** Lovable uses OAuth by default. After you click **Add & authorize**, you’ll be prompted to authorize.
      * **Bearer token or API key:** If you want, you can also authenticate using a bearer token (PAT, read more [here](../#personal-access-token-api-key)).
   2. **Add server**. The AI Context Flow MCP server now appears in your list of chat connectors and can provide contextual data for builds.

#### Use it

Once connected, reference your Plurality memory directly in Lovable prompts. For example:

> _"Build a dashboard using all the requiremtents in my X project bucket"_

Your memory buckets, documents, and notes act as live data for the apps you generate.

#### Verify

In a Lovable prompt, ask the builder to read from Plurality. If it returns content from your buckets, the connection is working.

#### Troubleshoot

**MCP option missing in Connectors.** You're on a Free plan. MCP requires a paid plan.

**OAuth completes but Lovable doesn't see the tools.** Refresh the project page after authentication.
