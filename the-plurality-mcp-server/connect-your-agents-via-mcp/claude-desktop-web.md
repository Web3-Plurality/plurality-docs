---
description: 'Last updated: April, 2026'
---

# Claude Desktop/Web

> **TL;DR** Paid plans connect via the Connectors UI in Settings. Free plans on Desktop connect via the `mcp-remote` config bridge.

Claude supports MCP on both free and paid plans, but the setup paths are different. Use the section that matches your plan.

#### Prerequisites

* **Paid plan path:** A Claude paid plan (Pro, Max, Team, or Enterprise). Works on both Desktop and Web.
* **Free plan path:** Claude Desktop installed (Mac or Windows). Node.js installed. Free plan only works on Desktop, not Web.

#### Setup — paid plans (Pro, Max, Team, Enterprise)

1. Open **Settings → Connectors**.
2. Click **Add** **Custom Connector**  and paste: `https://app.plurality.network/mcp`
3. Claude opens a browser window for OAuth login. Sign in with your Plurality account.
4. Once authenticated, the Plurality tools appear in the chat input.

#### Setup — free plan (Desktop only)

Free-plan users can connect the Desktop app via the [`mcp-remote`](https://www.npmjs.com/package/mcp-remote) bridge.

1. Open the Claude Desktop config file:
   * **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
   * **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`
2. Add the `mcpServers` block:

```json
{
  "mcpServers": {
    "plurality-memory": {
      "command": "npx",
      "args": ["mcp-remote", "https://app.plurality.network/mcp"]
    }
  }
}
```

> **Windows note:** if you see "Connection closed" errors, wrap the command with `cmd /c`:
>
> ```json
> {
>   "command": "cmd",
>   "args": ["/c", "npx", "mcp-remote", "https://app.plurality.network/mcp"]
> }
> ```

3. **Fully restart Claude Desktop** — quit and reopen, not just close the window.
4. On first use, `mcp-remote` opens your browser for OAuth login. After authenticating, tokens are cached locally.

#### Verify

Look for the connectors icon in Claude's chat input. The Plurality memory connector should appear in the list.

In a new chat, ask: _"What's in my Plurality memory?"_

If it calls the `get_user_memory_buckets` tool and returns your buckets, you're connected.

#### Troubleshoot

**Tools don't appear after adding the connector.** Fully quit Claude (don't just close the window) and reopen.

**Free plan: `mcp-remote` errors with "Connection closed."** On Windows, use the `cmd /c` wrapper shown above.

**Free plan: `npx` not found.** Install [Node.js](https://nodejs.org). The `mcp-remote` bridge requires it.

**OAuth completes but tools still missing.** Check the URL in your config — no trailing slash, no extra characters should be there.
