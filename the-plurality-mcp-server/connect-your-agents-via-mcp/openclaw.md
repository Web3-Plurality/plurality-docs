---
description: 'Last updated: April, 2026'
---

# OpenClaw

> **TL;DR** Add the Plurality MCP Server to your `openclaw.json`, restart OpenClaw, and authenticate. Your OpenClaw agent gets read and write access to your memory buckets.

#### Prerequisites

* A Plurality account
* OpenClaw installed and running (see [OpenClaw's docs](https://docs.openclaw.ai))
* Edit access to your `openclaw.json` config file
* An access token from the Memory Studio

#### Why connect OpenClaw to Plurality

OpenClaw runs continuously and executes tasks autonomously — cron jobs, event listeners, background workflows. By default, every task starts from a blank slate. Connecting it to the Plurality MCP Server lets every OpenClaw run draw on your accumulated context: project history, past decisions, preferences, ongoing notes.

In practice: an OpenClaw agent that reviews your inbox each morning, drafts replies in your usual voice, and stores its summaries back into your memory bucket. The agent stays consistent across runs because the context is yours, not the agent's session.

#### Setup

**Find your config file**

OpenClaw stores its config at `~/.openclaw/openclaw.json` by default:

| OS      | Path                                               |
| ------- | -------------------------------------------------- |
| macOS   | `~/.openclaw/openclaw.json`                        |
| Linux   | `~/.openclaw/openclaw.json`                        |
| Windows | `C:\Users\<your-username>\.openclaw\openclaw.json` |

If you've set the `OPENCLAW_CONFIG_PATH` environment variable to a custom location, edit that file instead.&#x20;

**Add the Plurality MCP Server with a Personal Access Token (headless setups)**

For servers, CI pipelines, or any environment where opening a browser isn't practical, use a Personal Access Token instead. Read more [here](../#personal-access-token-api-key) how to create PATs on the Memory Studio.

Open the config file and add the Plurality MCP Server to the `mcp` section. Create one if its not there

```json
...
"mcp": {
    "servers": {
      "plurality": {
        "url": "https://app.plurality.network/mcp",
        "transport": "streamable-http",
        "headers": {
          "Authorization": "Bearer plur_pat_your-access-token"
        }
      }
    }
  }
...
```

(optional) Set the token as an environment variable rather than hard-coding it:

```
export PLURALITY_PAT=plk_<your_token>
```

Restart OpenClaw to pick up the new config (`openclaw gateway restart`), or wait for hot reload.

> The Gateway also watches the config file and applies most changes automatically. If hot reload picks up the change, you don't need to restart manually.

#### Verify

To verify, you can run the command `openclaw mcp list` , it should show the added mcp server.&#x20;

To check further, open the openclaw UI and open chat. Inside the chat, write

```
List every tool you have access to, 
including the MCP server each one comes from. Don't skip any.
```

This should return all the tools of the mcp server.

#### Use it

Once connected, the Plurality tools are available to your OpenClaw agent in the same way as any other MCP tool. A few practical patterns:

* **Read context into a task.** _"Look up what I know about Project X in Plurality before drafting this email."_
* **Save context from a task.** _"After summarizing today's meetings, save the summary to my Work bucket."_
* **Cross-tool continuity.** Anything OpenClaw saves is immediately available in Claude, ChatGPT, Cursor — and vice versa.

#### Troubleshoot

**OpenClaw doesn't see the Plurality tools after restart.** Confirm the JSON is valid (a missing comma will silently disable the entry). Check the URL is exactly `https://app.plurality.network/mcp` with no trailing slash.

**`401 Unauthorized` on every call.** Either the PAT expired or the PAT is invalid.Regenerate the token in your memory studio and update the environment variable.

**Tools call slowly or time out.** Semantic search on large buckets can exceed default timeouts. Increase the timeout settings in `openclaw.json`.
