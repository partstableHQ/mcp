# PartsTable MCP server

The parts reference for the secondary-market IT industry, as a remote MCP server. Look up, normalize, validate and cross-reference IT hardware part numbers. Every fact is cited to its source.

- **Endpoint:** `https://partstable.com/mcp`
- **Transport:** Streamable HTTP
- **Auth:** none. All tools are read-only lookups.
- **Official MCP Registry:** `com.partstable/partstable`

The calibrated layer behind these tools covers 1,122,337 parts and 2,001,002 cross-references (measured 2026-10-18).

## Install

There is nothing to download or build. Add the remote server to your MCP client.

**Cline / Claude Desktop / Cursor style config:**

```json
{
  "mcpServers": {
    "partstable": {
      "type": "streamableHttp",
      "url": "https://partstable.com/mcp"
    }
  }
}
```

**Clients that only speak stdio** can bridge with [`mcp-remote`](https://www.npmjs.com/package/mcp-remote):

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

## Tools

| Tool | What it does | Input |
|---|---|---|
| `normalize-pn` | Turns a messy part number into its standard form. Handles HPE (B21/001/spare), Dell (400-XXXX, DP/N) and IBM/Lenovo (FRU) formats. | `partNumber` |
| `validate-pn` | Checks a part number's structure and whether it exists in the PartsTable catalog. | `partNumber` |
| `get-part` | Returns the part record: identity, manufacturer, description, category, lifecycle, and government classification (NSN/FSC) when present. | `partNumber` |
| `get-substitutes` | Lists substitute and cross-referenced part numbers with their sources. | `partNumber` |
| `search-parts` | Looks up a batch of up to 25 part numbers at once. | `partNumbers` (array) |

## Try it

> "Normalize 720479b21 and tell me what it is."

> "Look up these three part numbers: 00HM821, P43019-B21, WS-X4991."

## Links

- Website: https://partstable.com
- Part pages: `https://partstable.com/parts/{PART-NUMBER}`
- Privacy: https://partstable.com/privacy
- Support: tony@partstable.com

This repository holds the listing and install docs only. The server is hosted by PartsTable Design LLC.

License: MIT
