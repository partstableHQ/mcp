# Installing the PartsTable MCP server (for AI agents)

This is a hosted remote server. Do not clone or build anything.

1. Add this entry to the MCP settings file (`cline_mcp_settings.json` in Cline):

```json
{
  "mcpServers": {
    "partstable": {
      "type": "streamableHttp",
      "url": "https://partstable.com/mcp",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

2. No API key or environment variables are needed.
3. Check the connection by calling `normalize-pn` with `{"partNumber": "720479b21"}`. The expected result contains `"720479-B21"` with manufacturer HP.

If the client cannot use Streamable HTTP, use the stdio bridge instead:

```json
{
  "mcpServers": {
    "partstable": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://partstable.com/mcp"]
    }
  }
}
```
