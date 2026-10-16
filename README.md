# GoVeda Patent MCP

Search patent records, read patent content, follow citations, and research prior art through GoVeda's hosted [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) service.

- Endpoint: `https://mcp.goveda.com/mcp`
- Transport: Streamable HTTP
- Authentication: browser OAuth sign-in with a GoVeda account

This repository contains the Cursor plugin, connection configuration, and documentation. It does not contain the hosted server. No Node.js, bridge process, API key, or token is required in the Cursor configuration.

## Connect Cursor

For a project, merge the following entry into `.cursor/mcp.json`. For all projects, use `~/.cursor/mcp.json`. Preserve any existing server entries.

```json
{
  "mcpServers": {
    "goveda-patent": {
      "url": "https://mcp.goveda.com/mcp"
    }
  }
}
```

Open Cursor's **Customize** page, locate the MCP server, enable it if needed, and complete **Connect** / browser sign-in when prompted. Review GoVeda's consent screen before approving. Cursor discovers the OAuth configuration; do not add an Authorization header or embed OAuth client secrets.

An administrator may restrict MCP servers or plugin imports. See [Cursor's MCP documentation](https://cursor.com/docs/mcp).

### Cursor plugin preview

The plugin manifest is `.cursor-plugin/plugin.json`; the remote server configuration is `mcp.json` at the repository root. A manifest in this repository does not establish marketplace approval.

This preview has passed static checks and a separate hosted-service protocol smoke test. Installation, authentication, and tool use inside Cursor remain unverified.

For local plugin testing, copy this version of the repository into `~/.cursor/plugins/local/goveda-patent/`, including the hidden `.cursor-plugin` directory. Restart Cursor or run **Developer: Reload Window**, then inspect **Customize**. Local plugin imports must be allowed. Do not also configure the same server manually: use one installation route to avoid duplicate connections. See [Cursor's local testing instructions](https://cursor.com/docs/plugins#test-plugins-locally).

If an approved marketplace listing becomes available, install it from **Customize**, select the desired scope, and authenticate with GoVeda.

## Account and usage

A GoVeda account is required. Hosted tool calls can consume GoVeda Subscription credits, shared with the GoVeda web app. Research tools can create search history, reports, or asynchronous jobs. Review the current [MCP pricing and account requirements](https://www.goveda.com/en/docs/agent/mcp-pricing) before running tools; read-only does not mean free. Do not assume every account is eligible for a new trial.

Current tool inputs, limits, supported data, and costs are maintained in the [MCP tool reference](https://www.goveda.com/en/docs/agent/mcp-tools) and pricing documentation. The authenticated server catalog determines which tools your client can use.

## Example prompts

Use public patent material when trying the connection:

- “Read the title, abstract, and filing date of US-10000000-B2. Include the publication reference and state any missing data.”
- “Find patent classifications related to solid-state batteries.”
- “Search for five patents about solid-state battery electrolytes for electric vehicles. Include publication numbers and source links, and distinguish retrieved facts from your interpretation.”

Patent research and AI-generated assessments are informational. Search coverage can be incomplete; these outputs do not establish novelty, patentability, validity, infringement, or freedom to operate. Seek qualified professional review for legal decisions.

## Troubleshooting and disconnecting

- **Sign-in canceled or denied:** return to Customize and reconnect when ready. Do not paste access tokens into chat or configuration.
- **Expired or revoked access:** reconnect if Cursor cannot refresh the connection. If an error continues, provide support with the error code and approximate time, without credentials or private queries.
- **Account, credits, or service error:** follow the server's error message and consult the current account/pricing documentation or support. Avoid repeatedly retrying a tool that may create jobs or consume credits.
- **Disable:** toggle the MCP server off in Customize to stop exposing its tools to chat.
- **Remove:** uninstall a marketplace plugin through Customize, or remove only the manually added server entry. For a local preview, remove the test plugin directory you created after disabling it. Preserve unrelated configuration.

Disabling or uninstalling a client is not proof that server-side authorization was revoked. GoVeda's MCP exposes OAuth token revocation; client support and behavior vary. For help ending authorization, contact [GoVeda support](https://www.goveda.com/contact). Never send support an access or refresh token.

## Other MCP clients

Use the current [GoVeda connection guide](https://www.goveda.com/en/docs/agent/mcp) for Claude, ChatGPT, and other supported clients. This avoids duplicating client-specific setup that may change.

## Privacy, support, and license

Tool arguments, including search text or patent references you send, are processed by GoVeda. Only send material you are authorized to share. The plugin contains no local executables, hooks, telemetry, or bundled skills; the hosted service's data handling is described in its privacy policy.

- [Privacy Policy](https://www.goveda.com/privacy)
- [Terms of Service](https://www.goveda.com/terms)
- [Support](https://www.goveda.com/contact)
- [Connection guide](https://www.goveda.com/en/docs/agent/mcp)

Repository files are licensed under [Apache-2.0](LICENSE). Hosted-service access remains subject to GoVeda's Terms of Service and applicable account limits. GoVeda branding is used to identify this integration; no Cursor endorsement is claimed.
