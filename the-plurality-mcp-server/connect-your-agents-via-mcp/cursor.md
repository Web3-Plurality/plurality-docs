---
description: 'Last updated: April, 2026'
---

# Cursor

> **TL;DR** Edit one JSON file, restart Cursor, OAuth on first use.

#### Prerequisites

* Cursor installed

#### Setup

Cursor supports global config (all projects) or project-level config.

**Global setup.** Edit `~/.cursor/mcp.json` (create the file if it doesn't exist):

```json
{
  "mcpServers": {
    "plurality-memory": {
      "url": "https://app.plurality.network/mcp"
    }
  }
}
```

**Project-level setup.** Create `.cursor/mcp.json` in your project root with the same content.

After saving the config, **fully restart Cursor** (quit and reopen, not just close the window).

#### Verify

Navigate to **Settings → MCP**. The `plurality-memory` server should show a green active status.

On first use, Cursor opens your browser to complete OAuth. After authentication, the tools are available in your chat input.

#### Troubleshoot

**Server shows red / inactive in Settings → MCP.** Check the JSON — most issues are typos or missing commas. Confirm the URL is exactly `https://app.plurality.network/mcp`.

**OAuth never opens.** Try sending a chat message — Cursor triggers OAuth lazily on first tool call.

**Tools work in one project but not another.** You added project-level config in one and not the other. Move the config to `~/.cursor/mcp.json` for global access.
