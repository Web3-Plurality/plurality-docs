---
description: 'Last updated: April, 2026'
---

# GitHub Copilot

### GitHub Copilot (VS Code)

> **TL;DR** Add the Plurality MCP Server through VS Code's native MCP configuration, then use it from Copilot Chat in Agent mode.

#### Prerequisites

* VS Code **1.99 or later**
* A paid GitHub Copilot subscription
* GitHub Copilot extension installed in VS Code

#### Setup

**Option A — UI**

1. Open VS Code and press `Cmd+Shift+P` (macOS) or `Ctrl+Shift+P` (Windows/Linux).
2. Run **MCP: Add Server**.
3. Select **HTTP (HTTP or Server-Sent Events)**.
4. Enter the server URL: `https://app.plurality.network/mcp`
5. Name the server: `plurality-memory`
6. Choose **User** settings (all projects) or **Workspace** settings (this project only).

**Option B — `settings.json`**

Add directly to your `settings.json`:

json

```json
{
  "mcp": {
    "servers": {
      "plurality-memory": {
        "type": "http",
        "url": "https://app.plurality.network/mcp"
      }
    }
  }
}
```

7. Open **GitHub Copilot Chat** and switch to **Agent mode**. The Plurality tools appear in the available tools list.
8. On first use, VS Code prompts you to authenticate via OAuth in your browser.

#### Verify

In Copilot Chat (Agent mode), ask: _"Search my Plurality memory for anything about \[topic]."_

If Copilot calls `search_memory` and returns results, you're connected.

#### Troubleshoot

**MCP: Add Server command not found.** Update VS Code to 1.99 or later.

**Tools missing in Copilot Chat.** Make sure you're in **Agent mode**, not Ask or Edit mode.

**OAuth completes but tools fail to load.** Reload the VS Code window (`Cmd/Ctrl+Shift+P → Developer: Reload Window`).
