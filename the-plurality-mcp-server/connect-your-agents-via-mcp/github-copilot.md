---
description: 'Last updated: April, 2026'
---

# GitHub Copilot

### GitHub Copilot (VS Code)

> **TL;DR** dd the Plurality MCP Server through VS Code's native MCP configuration with a Plurality PAT, then use it from Copilot Chat in Agent mode.

#### Prerequisites

* VS Code **1.99 or later**
* A paid GitHub Copilot subscription
* GitHub Copilot extension installed in VS Code
* A Plurality personal access token. Read how to do it [here](../#personal-access-token-api-key)

**Setup**

1. Open VS Code and press `Cmd+Shift+P` (macOS) or `Ctrl+Shift+P` (Windows/Linux).
2. Run **MCP: Add Server**.
3. Select **HTTP (HTTP or Server-Sent Events)**.
4. Enter the server URL: `https://app.plurality.network/mcp`
5. Name the server: `plurality-memory`
6. Choose **User settings** (all projects) or **Workspace settings** (this project only).
7. It will then ask to authenticate from your account and open the app.plurality.network webpage. After authentication you return back to vscode.
8. If you want you can also edit the created mcp.json to authenticate via PAT.&#x20;

**Verify**

In Copilot Chat (Agent mode), ask: _"Search my Plurality memory for anything about \[topic]."_ If Copilot calls `search_memory` and returns results, you're connected.

**Troubleshoot**

* _`MCP: Add Server` command not found._ Update VS Code to 1.99 or later.
* _Tools missing in Copilot Chat._ Make sure you're in Agent mode, not Ask or Edit mode.
* _401 Unauthorized from the server._ Your PAT is invalid, expired, or missing required scopes — regenerate it in Plurality, then run **MCP: List Servers**, pick the server, and reset stored inputs to re-enter it.
* _Tools fail to load after entering the PAT._ Reload the VS Code window (`Cmd/Ctrl+Shift+P → Developer: Reload Window`).
