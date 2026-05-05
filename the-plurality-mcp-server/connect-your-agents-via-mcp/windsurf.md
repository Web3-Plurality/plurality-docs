---
description: 'Last updated: April, 2026'
---

# Windsurf

> **TL;DR** Edit one JSON file, restart Windsurf, OAuth on first use.

#### Prerequisites

* Windsurf installed
* Personal Access Token created on the Memory Studio

#### Setup

For remote http mcp connections, windsurf only allows with Personal Access Tokens (PATs).&#x20;

Read more [here](../#personal-access-token-api-key) on how to create one from Memory Studio.



1. Edit (or create) the raw mcp config file<br>
   * macOS: `~/.codeium/windsurf/mcp_config.json`
   * Windows: `%USERPROFILE%\.codeium\windsurf\mcp_config.json`

```json
{
  "mcpServers": {
    "plurality-memory": {
      "disabled": false,
      "headers": {
        "Authorization": "Bearer plur_pat_xxx"
      },
      "serverUrl": "https://app.plurality.network/mcp"
    }
  }
}
```

2. Restart Windsurf.
3. Open the Cascade panel (agent sidebar). The Plurality tools become available to the AI agent.
4. On first use, Windsurf opens your browser for OAuth login.

#### Verify

In Cascade, ask: _"List my Plurality memory buckets."_

If the agent calls `get_user_memory_buckets` and returns results, you're connected.

#### Troubleshoot

**Tools missing in Cascade.** Confirm the JSON key is `serverUrl` (not `url`) — Windsurf is picky about this.

**OAuth completes but no response.** Restart Windsurf fully and try again.

**Personal Access Token was correct.** Make sure the header name is exactly _Authorization_ and the value is _Bearer \<your access token starting with plur\_pat\_>_
