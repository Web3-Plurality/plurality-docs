---
icon: link-simple
---

# The Plurality MCP Server

> **TL;DR** The Plurality MCP Server exposes your memory buckets to any AI agent that speaks the Model Context Protocol. Connect once per tool, authenticate (via OAuth or a personal access token), and your context flows automatically — both ways.

### What is MCP?

The [Model Context Protocol](https://modelcontextprotocol.io) is an open standard, originally developed by Anthropic, for connecting AI models to external data and tools. Think of it as a universal adapter: any agent that speaks MCP can talk to any data source that speaks MCP, without custom integration work on either side.

MCP support is now standard across the agent ecosystem. Claude Desktop, Claude Code, Cursor, Windsurf, GitHub Copilot, LM Studio, Lovable, Replit, ChatGPT (via custom connectors), OpenClaw, and many others speak it natively.

### What the Plurality MCP Server does

The Plurality MCP Server is the bridge between your memory buckets and the AI tools you use. It runs at:

```
https://app.plurality.network/mcp
```

When an AI agent connects to this URL, it gains **read and write access** to your Plurality memory layer — your documents, notes, conversations, and files stored across memory buckets — bounded by the permissions you set.

The server is the _only_ component that talks to outside agents. Your memory buckets never leave your control; the MCP Server retrieves only what an agent is permitted to see, in the moment it's requested.

### How it fits

```
   ┌──────────────────────────────────────┐
   │  Your AI agent (Claude, Cursor, ...) │
   └─────────────────┬────────────────────┘
                     │  MCP request
                     ▼
   ┌──────────────────────────────────────┐
   │  Plurality MCP Server                │
   │  ─ verifies authentication           │
   │  ─ checks permissions                │
   │  ─ fetches/writes context            │
   └─────────────────┬────────────────────┘
                     │
                     ▼
   ┌──────────────────────────────────────┐
   │  Your memory buckets                 │
   └──────────────────────────────────────┘
```

### What's exposed

The Plurality MCP Server exposes the following tools to connected agents:

| Tool                          | Description                                            |
| ----------------------------- | ------------------------------------------------------ |
| `get_user_memory_buckets`     | List all memory buckets for the user                   |
| `list_items_in_memory_bucket` | List stored items in a specific bucket (metadata only) |
| `search_memory`               | Semantic search across buckets with relevance scoring  |
| `read_context`                | Read the full content of a stored item (paginated)     |
| `save_memory`                 | Save text content to a specific memory bucket          |
| `save_conversation`           | Save a chat history to a memory bucket                 |
| `create_memory_bucket`        | Create a new memory bucket                             |

Connected agents can **read** your context and **write** new context back to your buckets — context saved from Cursor is immediately available in Claude or ChatGPT, with no manual syncing.

### Authentication

The Plurality MCP Server supports two authentication methods. Most users will use OAuth; API keys are available for advanced and programmatic use cases.

#### OAuth 2.1 (default)

OAuth is the recommended option for connecting interactive AI tools — Claude Desktop, ChatGPT, Cursor, Windsurf, GitHub Copilot, Lovable, Replit, LM Studio, OpenClaw, and others.

When you connect a tool, it opens a browser window and redirects you to Plurality's login flow. After you authenticate, the tool receives an access token scoped to your account. The tool stores this token locally; Plurality never sees the tool's session.

**Why use it:**

* No credentials to copy or paste
* Easy to revoke (sign tools out from your Plurality dashboard)
* Standard flow supported natively by every major MCP client

The Plurality MCP Server implements OAuth 2.1 with **Dynamic Client Registration (DCR)**, which is what allows any compliant MCP client to connect without prior coordination.

#### Personal Access Token (API key)

For environments where OAuth is impractical — CI pipelines, scripts, self-hosted agents, headless deployments — the Plurality MCP Server also accepts personal access tokens.

**To use a PAT:**

1. Generate a token in your Plurality dashboard under **`[CONFIRM: Settings → Developer → Personal Access Tokens]`**.
2. In your MCP client's configuration, add an `Authorization` header:

```
Authorization: Bearer plk_<your_token>
```

`[CONFIRM: actual token prefix and header format]`

**Why use it:**

* Works in environments without a browser
* Easy to scope to specific buckets or operations
* Can be set per-environment (different tokens for dev/staging/prod)

**Treat PATs like passwords** — never commit them to source control, and rotate them when team members leave.

### Permissions and security

Three things to know:

1. **Per-agent permissions.** Each connected agent has its own access scope. Granting Claude Desktop access to your _Work_ bucket doesn't grant any other tool access to it.
2. **Per-bucket permissions.** Buckets are independent units. An agent permitted on one is not automatically permitted on others.
3. **Revocation is instant.** Pull permission in your Plurality dashboard and the agent loses access on its next request.

Tokens (both OAuth and PAT) are cached locally by the client. Plurality never receives, stores, or sees the credentials of the AI tools you connect.
