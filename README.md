# GoVeda Patent MCP Server

AI-powered patent intelligence for search & analysis via the [Model Context Protocol (MCP)](https://modelcontextprotocol.io/).

Search and analyze **220M+ global patents** with semantic search, prior art discovery, novelty/patentability reports, and full patent content retrieval — directly from Claude, ChatGPT, and other MCP-compatible AI assistants.

**Endpoint:** `https://mcp.goveda.com/mcp`
**Transport:** Streamable HTTP
**Authentication:** OAuth 2.0 (automatic browser sign-in)

## Quick Start

### Claude Desktop / claude.ai

Settings > Connectors > Add custom connector:

- **Name:** GoVeda Patent
- **URL:** `https://mcp.goveda.com/mcp`

OAuth authentication opens automatically in your browser.

### Claude Code

```bash
claude mcp add goveda-patent --transport http https://mcp.goveda.com/mcp
```

### ChatGPT

Settings > Apps > Advanced > Enable Developer Mode. Add MCP server with URL `https://mcp.goveda.com/mcp` and OAuth authentication.

### Cursor / Windsurf (mcp-remote bridge)

For clients that only support stdio transport:

```json
{
  "mcpServers": {
    "goveda-patent": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.goveda.com/mcp"]
    }
  }
}
```

Requires Node.js installed. `mcp-remote` handles OAuth and protocol bridging.

### VS Code / GitHub Copilot

Add to `.vscode/mcp.json`:

```json
{
  "servers": {
    "goveda-patent": {
      "type": "streamable-http",
      "url": "https://mcp.goveda.com/mcp"
    }
  }
}
```

## Tools

### Search & Discovery

| Tool | Description | Cost |
|------|-------------|------|
| `search_patents` | Semantic search across 220M+ patents by technology description or concept | ~50-320 credits |
| `get_prior_art` | Find prior art for a known patent by publication number | ~690 credits |
| `get_search_status` | Poll async search/prior art progress and retrieve results | Free |

### Reports

| Tool | Description | Cost |
|------|-------------|------|
| `generate_report` | AI-powered novelty/patentability assessment for an invention idea | 720 credits |
| `get_report_status` | Poll async report generation progress | Free |
| `get_report_summary` | Executive summary with patentability verdict | Free |
| `get_report_patent_analysis` | Detailed claim-by-claim comparison with cited prior art | Free |

### Patent Content

| Tool | Description | Cost |
|------|-------------|------|
| `get_patent` | Retrieve specific patent sections by publication number | 1 credit |
| `batch_get_patents` | Retrieve multiple patents in one call | 1 credit/patent |

Available sections: `abstract`, `claims`, `description`, `dates`, `parties`, `classifications`, `legal_status`, `citations`, `family`, or `all`.

### Account

| Tool | Description | Cost |
|------|-------------|------|
| `get_usage` | Check remaining credit balance and billing period | Free |
| `start_free_trial` | Activate 14-day trial with 10,000 credits | Free |

## Example Prompts

**Patent search:**
> "Search for patents about wireless charging for electric vehicles"

**Prior art analysis:**
> "Find prior art for patent US-20230001234-A1"

**Patent content:**
> "Show me the abstract and claims of US-11234567-B2"

**Novelty report:**
> "Generate a novelty report for: A solar panel with self-cleaning nano-coating that activates upon detecting dust accumulation using piezoelectric sensors"

**Credit check:**
> "Check my remaining credits"

## Pricing

New users get a **14-day free trial with 10,000 credits** — no credit card required. Credits are shared between the MCP server and the [GoVeda web app](https://www.goveda.com).

See [goveda.com/pricing](https://www.goveda.com/pricing) for plans.

## Important Notes

- Reports are AI-generated for informational purposes only. Professional legal review is recommended for patent decisions.
- All tools include MCP safety annotations (`readOnlyHint`, `destructiveHint`, `title`).
- Responses are truncated to 8,000 characters per field to limit data exposure.

## Links

- [GoVeda](https://www.goveda.com) — Web application
- [Documentation](https://www.goveda.com/docs/agent/mcp) — Full MCP server documentation
- [Privacy Policy](https://www.goveda.com/privacy)
- [Terms of Service](https://www.goveda.com/terms)
- [Support](mailto:support@goveda.com)

## License

This repository contains documentation and configuration for the GoVeda Patent MCP Server. The server itself is a hosted service at `mcp.goveda.com`. See [Terms of Service](https://www.goveda.com/terms) for usage terms.
