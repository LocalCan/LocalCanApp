# Installing the LocalCan MCP server

LocalCan's MCP server is built into the `localcan` CLI. Install LocalCan first, then register `localcan mcp` as a stdio server with your MCP host.

## 1. Install LocalCan

- **macOS**: download the app from [localcan.com/download](https://www.localcan.com/download) and open it. When it asks, install the command line tools (or enable them later in Settings → Command-line tools).
- **Windows**: download the installer from [localcan.com/download](https://www.localcan.com/download) and run it. Install the command line tools when asked.
- **Linux** (CLI only):

```sh
curl -fsSL https://localcan.com/install.sh | sh
```

Verify with `localcan version`.

## 2. Register the MCP server

Claude Code:

```sh
claude mcp add --scope user localcan -- localcan mcp
```

Codex:

```sh
codex mcp add localcan -- localcan mcp
```

Other hosts (Cursor, Claude Desktop, Windsurf, Cline, VS Code) use the standard stdio config:

```json
{
  "mcpServers": {
    "localcan": {
      "command": "localcan",
      "args": ["mcp"]
    }
  }
}
```

GUI apps may need the absolute path to the binary, for example `/Users/you/.localcan/bin/localcan` on macOS.

## 3. Notes

- LocalCan must be running (the desktop app, or `localcan start` on Linux).
- Reading captured traffic works out of the box. Write tools (creating Public URLs, publishing Snapshots, setting passwords) are off by default. Enable them with `localcan mcp access read_write`.
- Sensitive headers (Authorization, cookies, API keys) are redacted from tool responses by default.
- Full documentation: [localcan.com/docs/ai-agents/mcp](https://www.localcan.com/docs/ai-agents/mcp)
