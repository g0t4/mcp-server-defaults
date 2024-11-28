# mcp-server-macos-defaults MCP server

MCP server for reading/writing macOS defaults (settings)

## Components

### Tools

- `list-domains`:
  - equivalent to running `defaults domains`
- `find`:
  - equivalent to running `defaults find <word>`
- `defaults-read`:
  - equivalent to running `defaults read <domain> <key>`
  - if `key` is not provided, the entire domain is read
- `defaults-write`:
  - equivalent to running `defaults write <domain> <key> <value>`

## Quickstart

### Install

#### Claude Desktop

On MacOS: `~/Library/Application\ Support/Claude/claude_desktop_config.json`
On Windows: `%APPDATA%/Claude/claude_desktop_config.json`

<details>
  <summary>Development/Unpublished Servers Configuration</summary>
  ```
  "mcpServers": {
    "mcp-server-macos-defaults": {
      "command": "uv",
      "args": [
        "--directory",
        "/path/to/mcp-server-macos-defaults",
        "run",
        "mcp-server-macos-defaults"
      ]
    }
  }
  ```
</details>

<details>
  <summary>Published Servers Configuration</summary>
  ```
  "mcpServers": {
    "mcp-server-macos-defaults": {
      "command": "uvx",
      "args": [
        "mcp-server-macos-defaults"
      ]
    }
  }
  ```
</details>

## Development

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
npx @modelcontextprotocol/inspector uv --directory /path/to/mcp-server-macos-defaults run mcp-server-macos-defaults
```


Upon launching, the Inspector will display a URL that you can access in your browser to begin debugging.
