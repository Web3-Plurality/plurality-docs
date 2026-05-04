---
description: 'Last updated: April, 2026'
---

# Replit

> **TL;DR** Add the Plurality MCP Server as a tool inside the Replit Agent.

#### Prerequisites

* A Replit account
* A Replit project open with the Agent enabled

#### Setup

1. Open a Replit project and start the **Agent**.
2. Click the **Tools** icon in the agent panel.
3. Select **Add tool → MCP Server**.
4. Enter the server URL: `https://app.plurality.network/mcp` and confirm.
5. Complete OAuth authentication in the browser prompt.
6. Plurality tools become available to the agent for code generation and editing tasks.

#### Verify

Ask the Replit Agent: _"Look up notes from my Plurality memory about \[project]."_

If the agent uses `search_memory` and returns content, you're connected.

#### Troubleshoot

**Tools icon missing.** Make sure the Agent is running, not just the project.

**OAuth window closes without completing.** Re-run **Add tool → MCP Server** and follow the prompt to the end.
