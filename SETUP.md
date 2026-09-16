# Setting up SOKI

SOKI is a hosted MCP server. There is nothing to install and no API key to paste.
The first time a tool is used, the client opens a browser for sign-in and the
connection is remembered after that.

## Steps

1. The `soki` MCP server is already configured by this plugin
   (`https://mcp.kitemir.jp/mcp`, streamable HTTP).
2. On first use the client starts an OAuth 2.1 flow. A browser window opens at
   `mcp.kitemir.jp`. Sign in, or create an account there — it is free and takes
   a couple of minutes. Google sign-in is available.
3. Approve the consent screen. It states plainly which tools may read memories
   and which may write them.
4. That is the whole setup. From then on, just talk normally.

## If something goes wrong

- **The browser never opens** — the client may not support remote MCP OAuth.
  Check that it is up to date.
- **"Unknown tool" after an update** — the tool list is fixed when a conversation
  connects. Start a new conversation.
- **It answers but remembers nothing** — the account is connected but has no
  observations yet. SOKI only knows what has been said to it. Try the
  `import-notes` skill in this plugin to seed it from existing notes.

## Important

⚠️ SOKI cannot be used together with an AI's own built-in memory feature.
Two memories that do not know about each other will contradict one another.
Turn the built-in memory off, or do not use SOKI.

Full documentation: https://mcp.kitemir.jp/
