# gpt-researcher-mcp MCP server

A MCP server for gpt-researcher

This is just a MCP wrapper for gpt-researcher.

This project, gpt-researcher-mcp, is a wrapper extension built on top of the open-source project gpt-researcher.
The original gpt-researcher was developed by Assaf Elovic, and I am not the original author.

gpt-researcher is an automated research assistant that performs web searches, summarizes information, and generates structured reports based on a given query.
This wrapper (gpt-researcher-mcp) is designed to make the original tool more suitable for integration into MCP or similar workflows.

## Quickstart

### Install

#### Claude Desktop

On MacOS: `~/Library/Application\ Support/Claude/claude_desktop_config.json`
On Windows: `%APPDATA%/Claude/claude_desktop_config.json`

  ```
    "gpt-researcher-mcp": {
      "command": "npx",
      "args": ["-y", "gpt-researcher-mcp"],
      "env": {
        "llm_provider": "google_genai",
        "GOOGLE_API_KEY": "your key",
        "FAST_LLM": "google_genai:gemini-1.5-flash",
        "SMART_LLM": "google_genai:gemini-1.5-pro",
        "STRATEGIC_LLM":"google_genai:gemini-1.5-pro",
        "EMBEDDING": "google_genai:models/text-embedding-004",
        "TAVILY_API_KEY": "your key"
      }
    }
  ```

## Development
<details>
### Building and Publishing

To prepare the package for distribution:

1. Sync dependencies and update lockfile:
```bash
uv sync
```

2. Build package distributions:
```bash
uv build
```

This will create source and wheel distributions in the `dist/` directory.

3. Publish to PyPI:
```bash
uv publish
```

Note: You'll need to set PyPI credentials via environment variables or command flags:
- Token: `--token` or `UV_PUBLISH_TOKEN`
- Or username/password: `--username`/`UV_PUBLISH_USERNAME` and `--password`/`UV_PUBLISH_PASSWORD`

### Debugging

Since MCP servers run over stdio, debugging can be challenging. For the best debugging
experience, we strongly recommend using the [MCP Inspector](https://github.com/modelcontextprotocol/inspector).


You can launch the MCP Inspector via [`npm`](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) with this command:

```bash
npx @modelcontextprotocol/inspector uv run gpt-researcher-mcp
```

Upon launching, the Inspector will display a URL that you can access in your browser to begin debugging.
</details>