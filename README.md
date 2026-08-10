# phrase-mcp-registry

Publishing plumbing for the [MCP Registry](https://registry.modelcontextprotocol.io) listing of
the hosted Phrase MCP server (`io.github.phrase/mcp`).

This repo does not contain the MCP server implementation. It exists so that publishing to the
registry can be authenticated via GitHub Actions OIDC as a member of the `phrase` org, which the
registry uses to authorize the `io.github.phrase/*` namespace.

- `server.json` — the registry listing (hosted remotes, description, etc.)
- `.github/workflows/publish-mcp.yml` — validates and publishes `server.json` on push to `main`,
  or on-demand via "Run workflow" in the Actions tab.

The actual Phrase MCP server endpoints are documented at
[developers.phrase.com/en/mcp-server](https://developers.phrase.com/en/mcp-server).
