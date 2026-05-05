---
description: 'Last updated: April, 2026'
---

# LM Studio

> **TL;DR** LM Studio 0.3.5+ supports MCP, so locally-running models can call Plurality tools.

#### Prerequisites

* LM Studio **0.3.5 or later**
* A loaded model with tool calling capability (Mistral, Llama 3.1+, Qwen 2.5, or similar)
* Plurality access token from memory studio. Read [here](../#personal-access-token-api-key) how to create it.

#### Setup

1. Open LM Studio and navigate to the **Developer** tab.
   * If you don't see it, enable Developer Mode in **Settings → Advanced**.
2. Click on mcp.json and add the following json

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

```json
{
  "mcpServers": {
    "plurality-memory": {
      "url": "https://app.plurality.network/mcp",
      "headers": {
        "Authorization": "Bearer <plur_pat_your-acces-token"
      }
    }
  }
}
```

3. Make sure require authentication is turned on in server settings.\
   ![](<../../.gitbook/assets/image (8).png>)
4. Open a new chat and load a model with tool calling capability. Then on the right side in the program tab, make sure you turn plurality mcp on.&#x20;

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

5. Now chat to the model and it will call the plurality mcp tools where necessary.

#### Verify

Ask the model: _"Search my Plurality memory for \[something]."_

If the model invokes `search_memory` and returns results, you're connected.

#### Troubleshoot

**Model doesn't call tools even when enabled.** This is a model capability issue, not a connection issue. Some smaller models don't reliably call tools. Try Mistral, Llama 3.1+, or Qwen 2.5.

**Tools fail with timeout.** Local models can be slow on tool calls. Increase the request timeout in LM Studio's developer settings.
