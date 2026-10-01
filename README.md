# Linkup MCP Server for Zed

A Zed extension that runs the official [Linkup MCP server](https://github.com/LinkupPlatform/linkup-mcp-server) (`linkup-mcp-server` on npm) over stdio, giving Zed's Agent Panel real-time web search and page fetching with citable sources.

## Install

Open Zed's Extensions view (`zed: extensions`), search for **Linkup**, and click Install.

## Tools

| Tool | Description |
| --- | --- |
| `linkup-search` | Search the web in real time and return relevant, citable sources (title, URL, content). Supports `depth` (`standard` / `deep`), domain filters, date ranges, `maxResults` and images |
| `linkup-fetch` | Fetch any URL and return its content as clean markdown, with optional JavaScript rendering, image extraction and raw HTML |
| `linkup-research` | Start a long-running research task that investigates the web and returns a synthesized, cited answer |
| `linkup-get-research` | Poll a research task started with `linkup-research` |

Use `depth: "standard"` for most queries and `depth: "deep"` for complex, multi-step questions.

## Configuration

A Linkup API key is required. Create a free account at [app.linkup.so](https://app.linkup.so) and copy the key from your dashboard, then add it under the server's `settings` in `settings.json`:

```json
{
    "context_servers": {
        "mcp-server-linkup": {
            "settings": {
                "linkup_api_key": "YOUR_API_KEY"
            }
        }
    }
}
```

The key is passed to the server as the `LINKUP_API_KEY` environment variable.

## Without the extension

Zed natively supports remote MCP servers, so you can also connect to Linkup's hosted MCP server directly in `settings.json`:

```json
{
    "context_servers": {
        "linkup": {
            "url": "https://mcp.linkup.so/mcp",
            "headers": { "Authorization": "Bearer YOUR_API_KEY" }
        }
    }
}
```

## Using it in the Agent Panel

Open Settings → AI → MCP Servers and check the indicator dot next to the Linkup server — green means it's running. Tools can be toggled per agent profile. See the [Zed MCP docs](https://zed.dev/docs/ai/mcp) for details.

Linkup API docs: [docs.linkup.so](https://docs.linkup.so)

## License

MIT
