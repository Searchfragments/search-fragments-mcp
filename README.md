# Search Fragments

**The gate before your agent answers.** When a user half-remembers something your agent can't confidently place, one call returns a verdict on whether it can be reached, with the evidence or leads behind it, so the agent knows whether to answer, keep looking or say it can't place it, instead of inventing. Not for well-known facts, where normal search is faster.

**Tools:** `resolve_fragment`, `verify_claim`, `submit_resolution_feedback`
**Free. No signup required.**

Available in [Claude](https://claude.ai/directory/search-fragments), [Cursor](https://cursor.directory/plugins/search-fragments), [Raycast](https://www.raycast.com/raycast/model-context-protocol-registry) and [GitHub](https://github.com/mcp/com.searchfragments/search-fragments), or add the URL below to any MCP-compatible agent.

```json
{
  "mcpServers": {
    "search-fragments": {
      "url": "https://searchfragments.com/api/mcp"
    }
  }
}
```

## Why this exists

AI agents tend to become confidently wrong on fragmented queries: partial memories, indirect relationships, missing names. There's real signal in the fragment — enough for a model to recognize the pattern — but not enough to verify an answer from memory alone. The result is fluent, specific, and wrong.

Search Fragments is the gate between the question and the answer. Every `resolve_fragment` result carries a verdict, and each verdict is a move for the agent:

- **ORIGIN_OF_TRUTH** — found, and the evidence check passed. *Agent move: answer, and cite the sources.*
- **PARTIAL_ORIGIN** — leads worth following that could not be confirmed. *Agent move: follow them or show them; do not assert any of them as the answer.*
- **NOT_REACHABLE** — Search Fragments' search reached nothing to build on. *Agent move: say it can't place it and do not fill the gap.* This is a statement about what the search reached, not a claim that the thing cannot be found.

In a test against a baseline agent on 50 hard, under-documented fragments, the baseline fabricated three specific wrong answers with no hedge — Search Fragments declined honestly on all three. Full write-up: [searchfragments.com/agent-hallucinations](https://searchfragments.com/agent-hallucinations).

More on the design philosophy: [searchfragments.com/why](https://searchfragments.com/why).

## Server details

| | |
|---|---|
| Type | Remote, streamable-http MCP server |
| Endpoint | `https://searchfragments.com/api/mcp` |
| Tools | `resolve_fragment` (a verdict on a half-remembered fragment, with evidence or leads), `verify_claim` (check a specific factual claim against current sources), `submit_resolution_feedback` (report whether a result was right) |
| Auth | None required for basic use (free tier). OAuth 2.0 (Authorization Code + PKCE) available for authenticated use. |
| Registry | [MCP Registry](https://registry.modelcontextprotocol.io) — `com.searchfragments/search-fragments` |

See [`server.json`](./server.json) for the full MCP registry manifest.

## Links

- Website: [searchfragments.com](https://searchfragments.com)
- Privacy policy: [searchfragments.com/privacy](https://searchfragments.com/privacy)
- Terms: [searchfragments.com/terms](https://searchfragments.com/terms)
- Contact: hello@searchfragments.com

## License

MIT. See [LICENSE](./LICENSE).

## About this repository

This repository documents and points to the hosted Search Fragments MCP server. The server itself runs as a managed remote service — there's no local install; connect to the endpoint above from any MCP-compatible client.
