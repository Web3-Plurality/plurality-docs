---
description: 'Last updated: April, 2026'
---

# ChatGPT

> **TL;DR** Add `https://app.plurality.network/mcp` as a custom connector in ChatGPT settings. OAuth handles the rest.

#### Prerequisites

* A paid ChatGPT plan (Plus, Pro, Team, Enterprise, or Edu)
* To add MCP servers, a workspace admin must enable **Developer Mode** under \
  **Settings → Admin → Developer Mode**

#### Setup

1. Open **Settings → Apps → Create app**.
2. Enter a name (e.g. _Plurality Memory_) and paste the server URL: `https://app.plurality.network/mcp`
3. Save the connector. ChatGPT discovers the OAuth metadata automatically.
4. Start a new chat. On first use, ChatGPT opens a browser window for OAuth login.
5. Sign in with your Plurality account. Once authenticated, your memory buckets are available in conversation.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

#### Verify

In a new chat, ask: _"What memory buckets do I have in Plurality?"_

If ChatGPT calls the `get_user_memory_buckets` tool and returns your buckets, you're connected.

#### Troubleshoot

**"Add app" doesn't appear in settings.** You're probably on a Free plan, or Developer Mode hasn't been enabled by your workspace admin (Team/Enterprise).

**OAuth login window won't open.** Disable any browser pop-up blockers and try again.

**Connector shows "Disconnected" after authentication.** Sign out of the connector and re-add it. Confirm the URL is exactly `https://app.plurality.network/mcp` with no trailing slash.
