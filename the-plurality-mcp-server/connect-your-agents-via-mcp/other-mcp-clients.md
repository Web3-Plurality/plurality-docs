---
description: 'Last updated: April, 2026'
---

# Other MCP Clients

> **TL;DR** Any MCP client that supports streamable HTTP transport and OAuth 2.1 with Dynamic Client Registration can connect.

#### What you need from the client

The Plurality MCP Server uses standard MCP. Your client needs to support:

* **Streamable HTTP transport** (not just stdio-only clients)
* **OAuth 2.1 with Dynamic Client Registration (DCR)** for the recommended auth path
* _Or_ support for custom Authorization headers, if you'd rather use a Personal Access Token

#### Setup

Point your client at:

```
https://app.plurality.network/mcp
```

**With OAuth (recommended).** Most modern MCP clients handle OAuth automatically: configure the URL, and on first use the client opens a browser window for authentication. Tokens are cached locally by the client.

**With a Personal Access Token.** For headless environments — CI pipelines, scripts, server-side agents — generate a PAT in your Plurality dashboard and pass it as an Authorization header:

```
Authorization: Bearer <your_token>
```

See Authentication on the MCP Server page for the full PAT setup.

#### What the server exposes

Once connected, the client has access to seven tools: `get_user_memory_buckets`, `list_items_in_memory_bucket`, `search_memory`, `read_context`, `save_memory`, `save_conversation`, `create_memory_bucket`. See The Plurality MCP Server for details.

#### Verify

Call the `get_user_memory_buckets` tool. If it returns your buckets, you're connected.

#### Troubleshoot

**Client doesn't support OAuth DCR.** Use a Personal Access Token instead.

**Connection fails before authentication.** Confirm the URL is `https://app.plurality.network/mcp` exactly — no trailing slash, no extra characters.

**Tools list is empty after connection.** Authentication likely didn't complete. Check the client's logs for OAuth errors, or fall back to PAT auth.

**Need to test the connection without a client?** Use [`mcp-cli`](https://www.npmjs.com/package/mcp-cli) or any MCP debugger to hit the endpoint directly.
