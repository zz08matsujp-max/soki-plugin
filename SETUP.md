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
4. **Paste this one line into your AI's custom instructions.** Without it the
   AI will not call SOKI — it will quietly use its own memory instead. This is
   measured, not theoretical: of three first-time users, two recorded nothing
   until they pasted it.

   ```
   At the start of a conversation, call SOKI's profile_get. Record facts about me
   with memory_observe in SOKI, not in your own memory.
   ```

5. That is the whole setup. From then on, just talk normally.

## If something goes wrong

- **The browser never opens** — the client may not support remote MCP OAuth.
  Check that it is up to date.
- **"Unknown tool" after an update** — the tool list is fixed when a conversation
  connects. Start a new conversation.
- **It answers but remembers nothing** — the AI is reading from SOKI but not
  writing to it. Two causes, in order of how often they occur:
  1. **The custom instruction above has not been pasted.** This is the usual one.
  2. **The write tools are not permitted.** Allow the write/delete tools, not
     only the read-only ones. Read-only access produces exactly this symptom:
     it recalls, but never records.

  Open `/dashboard/connect` on mcp.kitemir.jp — it tells you which of the two
  you are in.

- **It is connected but has nothing to recall yet** — SOKI only knows what has
  been said to it. Try the `import-notes` skill in this plugin to seed it from
  existing notes.

## Important

⚠️ SOKI cannot be used together with an AI's own built-in memory feature.
Two memories that do not know about each other will contradict one another.
Turn the built-in memory off, or do not use SOKI.

Full documentation: https://mcp.kitemir.jp/
