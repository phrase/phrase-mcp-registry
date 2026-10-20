# Phrase MCP

Cursor plugin for the hosted [Phrase MCP server](https://developers.phrase.com/en/mcp-server):
language intelligence for translation, terminology, and quality, available directly in your editor.

This repo also holds the publishing plumbing for the
[MCP Registry](https://registry.modelcontextprotocol.io) listing (`io.github.phrase/mcp`).
It does not contain the MCP server implementation.

## Setup

1. Install the **Phrase** plugin in Cursor.
2. Open **Cursor Settings → MCP**. The plugin adds two servers:

   | Server      | Endpoint                     | Use if your Phrase account is in |
   | ----------- | ---------------------------- | -------------------------------- |
   | `phrase-eu` | `https://mcp.eu.phrase.com`  | the EU data center               |
   | `phrase-us` | `https://mcp.us.phrase.com`  | the US data center               |

3. **Enable the server that matches your Phrase data center and disable the other one.**
4. Connect to the enabled server and sign in with your Phrase account when prompted.

Not sure which region you are in? It is the region shown when you log in to Phrase, and the one
your organization admin chose at signup.

### Manual configuration

To use the server without the plugin, add one of the endpoints to `~/.cursor/mcp.json`
(or `.cursor/mcp.json` in a project):

```json
{
  "mcpServers": {
    "phrase": {
      "url": "https://mcp.eu.phrase.com"
    }
  }
}
```

Use `https://mcp.us.phrase.com` for the US region.

## Repo contents

- `.cursor-plugin/plugin.json` — Cursor plugin manifest
- `mcp.json` — remote MCP servers (EU and US)
- `assets/logo.png` — plugin logo
- `server.json` — MCP Registry listing
- `.github/workflows/publish-mcp.yml` — validates and publishes `server.json` on push to `main`,
  or on demand via "Run workflow" in the Actions tab. Authenticates via GitHub Actions OIDC as a
  member of the `phrase` org, which the registry uses to authorize the `io.github.phrase/*` namespace.

## Documentation

[developers.phrase.com/en/mcp-server](https://developers.phrase.com/en/mcp-server)
