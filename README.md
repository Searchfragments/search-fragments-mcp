# Search Fragments

**Resolve half-remembered queries without guessing.** A confident answer, a ranked shortlist, or an honest no. For when you half-remember something and can't place it. Half-remembered, cross-source queries usually take a dozen tabs and five rephrasings; Search Fragments collapses that into one call. Not for well-known facts, where normal search is faster.

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

Search Fragments is built to decline rather than guess. Every query resolves to one of three honest shapes:

- **Resolved** — a named answer, with confidence backed by evidence found.
- **Weighted Partial** — a ranked shortlist of candidates to decide by eye.
- **No Resolution** — an explicit "not resolvable from these clues," with no confidence claimed.

In a test against a baseline agent on 50 hard, under-documented fragments, the baseline fabricated three specific wrong answers with no hedge — Search Fragments declined honestly on all three. Full write-up: [searchfragments.com/agent-hallucinations](https://searchfragments.com/agent-hallucinations).

More on the design philosophy: [searchfragments.com/why](https://searchfragments.com/why).

## Server details

| | |
|---|---|
| Type | Remote, streamable-http MCP server |
| Endpoint | `https://searchfragments.com/api/mcp` |
| Tools | `resolve_fragment` (resolve a fragment), `verify_claim` (check a specific claim), `submit_resolution_feedback` (report whether a resolution was right) |
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
