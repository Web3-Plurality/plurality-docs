# Architecture at a Glance

> **TL;DR** OCL has four layers. \
> \
> 1\. Memory Buckets store your context. \
> 2\. AI Context Flow lets you manage and work with your context on any website. \
> 3\. The Plurality MCP Server exposes your context to MCP-compatible AI agents and tools. \
> 4\. Your AI agents and tools consume the context. \
> \
> You own everything in the bottom layer.

#### The four layers

```
                    ┌─────────────────────────────────┐
                    │  AI Agents                      │   The consumers
                    │  Claude · ChatGPT · Cursor      │
                    └────────────────┬────────────────┘
                                     │  MCP
   ┌─────────────────────────┐  ┌────▼─────────────────────┐
   │  AI Context Flow        │  │  Plurality MCP Server    │   The clients
   │  (Browser Extension)    │  │                          │
   │  capture · organize ·   │  │  exposes memory buckets  │
   │  permission · share     │  │  to AI agents            │
   └────────────┬────────────┘  └─────────────┬────────────┘
                │                             │
                │   read / write              │   read / write
                ▼                             ▼
   ┌──────────────────────────────────────────────────────┐
   │  Memory Buckets                                      │   The primitive
   │  user-owned · encrypted · portable                   │
   └──────────────────────────────────────────────────────┘
```

#### Layer 1 — Memory Buckets (the primitive)

A memory bucket is an encrypted, user-owned container of context. You can have multiple bucket for different parts of your life e.g. work, personal, health, a side project, and each one holds whatever context belongs to that slice of you.

→ Read more: Smart Profiles

#### Layer 2 — AI Context Flow (the product)

Memory buckets on their own are just storage. AI Context Flow is the product layer that makes them useful. It's a browser extension that helps you capture context from your activity, help you organize it into the right bucket, and lets you set permissions on what gets shared and with whom.

Think of it as the operating system for your context: capture, sort, permission, share.

→ Read more: AI Context Flow

#### Layer 3 — The Plurality MCP Server (the bridge)

The Plurality MCP Server speaks the [Model Context Protocol](https://modelcontextprotocol.io) — an open standard for connecting AI agents to data sources. By exposing your Memory Buckets through MCP, any compatible agent can request context from your profile and (with your permission) receive it in real time.

You don't paste your background into every new ChatGPT conversation. The agent asks; the MCP Server answers — under the rules you set.

→ Read more: The Plurality MCP Server

#### Layer 4 — Your AI agents (the consumers)

The agents you already use. Claude (Desktop and Code), ChatGPT, Cursor, Windsurf, GitHub Copilot, LM Studio, Lovable, Replit, OpenClaw, and any other tool that speaks MCP. They see the context you choose to share, and nothing else.

→ Read more: Connect Your Agents via MCP

#### How a request flows

When you ask Claude _"what was I working on last week?"_ and have setup the MCP connection:

1. **Claude** receives your question and recognizes it needs context.
2. **Claude** queries the **Plurality MCP Server** through the standard protocol.
3. **The MCP Server** checks which bucket has the relevant context and retrieves it from the correct bucket.&#x20;
4. The context is returned to Claude, which uses it to answer.<br>

Alternatively, if you are on a browser AI Agent and not using MCP.&#x20;

When you ask ChatGPT website _"what was I working on last week?"_ and then press "Optimize" button

1. **Your Prompt** is improved and the relevant context is fetched and added from the selected memory bucket
2. ChatGPT gives you improved answers because it now got a better, more contextual prompt with all the right details<br>

In both cases, you see a better, more fitting answer. The context never leaves your control without permission, and the answer is grounded in _your_ history — not a generic guess.
