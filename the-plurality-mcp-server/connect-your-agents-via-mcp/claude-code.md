---
description: 'Last updated: April, 2026'
---

# Claude Code

> **TL;DR** One CLI command, one OAuth flow.

#### Prerequisites

* Claude Code installed and logged in

#### Setup

In your terminal:

```
claude mcp add --transport http plurality-memory https://app.plurality.network/mcp
```

Then authenticate inside Claude Code:

```
> /mcp
```

This opens an OAuth browser window. Sign in with your Plurality account. Tokens are cached locally.

#### Verify

In a Claude Code session, ask: _"List my memory buckets."_

If Claude calls `get_user_memory_buckets` and returns results, you're connected.

#### Troubleshoot

**`claude: command not found`.** Make sure Claude Code is installed and on your `$PATH`.

**`/mcp` shows the server but no tools.** OAuth may not have completed. Run `/mcp` again and follow the browser prompt.

**Need to disconnect.** Run `claude mcp remove plurality-memory`.
