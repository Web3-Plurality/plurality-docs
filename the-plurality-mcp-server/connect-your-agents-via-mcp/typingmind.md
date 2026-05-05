---
description: 'Last updated: April, 2026'
---

# TypingMind

> **TL;DR** TypingMind doesn't use OAuth based MCP connections, therefore, the only way to authenticate is with Personal Access Tokens&#x20;

#### Prerequisites

* Personal Access Token from Memory Studio. Read [here](../#personal-access-token-api-key) how to create one.

#### Setup

1. Login to the TypingMind website.
2. On the left pane, go to **Plugins -> MCP Connectors -> Add Connector**.
3. Enter the **Server Url:** [https://app.plurality.network/mcp](https://app.plurality.network/mcp)
4. Enter the **Connection Name:** for e.g. plurality or ai context flow
5. Click on **Advanced Settings**&#x20;
6. Turn on the Custom HTTP Headers
   1. Header Name: Authorization
   2. Header Value: Bearer _plur\_pat-access-token_
7. Click **Create Connection**.

#### Use it

Once connected, reference your Plurality memory directly in chats. For example:

> _"List down all project requirements from bucket xxx"_

Your memory buckets, documents, and notes act as live data for the apps you generate.

#### Verify

In the chats when you reference something that needs information from your buckets and if it returns content from your buckets, the connection is working.

#### Troubleshoot

**Error in authentication.** Make sure you are using the correct access token

**Can't see the headers while making connection.** Make sure you click on advanced settings so the dropdown gets expanded, and then you turn on the Custom HTTP headers option.
