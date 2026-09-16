# GTD Brain — Gemini CLI extension

<img src="https://gtdbrain.com/gtdbrain/icon-512.png" alt="GTD Brain" width="96" align="right">

Your [Getting Things Done](https://gtdbrain.com/connect/gemini-cli?source=gemini-cli-extension)
board inside Gemini CLI. Capture what's on your mind straight to your Inbox without leaving the
terminal, pull up next actions by context, keep projects and Waiting For honest, and run a proper
weekly review — on the same board as the GTD Brain web, iOS, and Android apps, synced in real time.

The extension points Gemini CLI at GTD Brain's **hosted MCP server** (you sign in with an email
code — no API key, nothing to install) and adds a context file plus slash commands that teach
Gemini the method.

## What you get

- **16 MCP tools** — `capture`, `list_next_actions`, `list_projects`, `list_waiting_for`,
  `search_cards`, `create_card`, `update_card`, `move_card`, `archive_card`, context management,
  and more. Gemini calls them on its own when you talk about your tasks.
- **A `GEMINI.md` context file** that keeps Gemini honest: capture first and clarify later,
  verb-first next actions, every project has a next action, never answer about your board from
  memory.
- **Slash commands**
  - `/gtd:capture <text>` — one or many items straight to the Inbox
  - `/gtd:what-now [context]` — the two or three actions that fit right now
  - `/gtd:inbox-zero` — clarify every Inbox card, one at a time
  - `/gtd:weekly-review` — Get Clear · Get Current · Get Creative
  - `/gtd:waiting-for` — find stale delegated items and create follow-ups
  - `/gtd:setup` — check the connection and walk through sign-in
- **Safety by design** — Gemini can read, add, edit, move, and archive cards, but can never
  delete one. Archived cards stay recoverable.

## Install

```
gemini extensions install https://github.com/minosin/gtdbrain-gemini-extension
```

Then, inside Gemini CLI, sign in once:

```
/mcp auth gtdbrain
```

A browser tab opens on GTD Brain's sign-in page: enter your email, type the code we send you,
click **Allow**. A new email creates a free account. `/gtd:setup` confirms the connection.
Full guide: [gtdbrain.com/connect/gemini-cli](https://gtdbrain.com/connect/gemini-cli?source=gemini-cli-extension).

## Try it

- *Empty my head: I'll list everything on my mind, you capture each one to my inbox.*
- *What can I do right now? I'm at my computer with 30 minutes.*
- *Capture a card for each TODO comment you just found, with the file path in the note.*
- *Show my projects and flag any that have no next action.*
- *Show my Waiting For list — anything I should chase before the weekend?*

## Account and pricing

- No account needed in advance: signing in with a new email creates one.
- After connecting, free accounts get a handful of tool actions to try the connection. Ongoing
  use needs a GTD Brain subscription — the one subscription that also covers the web, iOS, and
  Android apps. Pricing at [gtdbrain.com](https://gtdbrain.com/?source=gemini-cli-extension#pricing).

## Privacy, terms, and support

- Privacy policy: https://gtdbrain.com/privacy
- Terms of use: https://gtdbrain.com/terms
- Data stays in your GTD Brain account; the extension itself contains no code that runs on your
  machine — only this configuration and the prompt text you can read in this repository.
- Support and security reports: **admin@minosin.com**. Disconnect at any time with
  `gemini extensions uninstall gtdbrain`.

## How it works

`gemini-extension.json` points Gemini CLI at `https://mcp.gtdbrain.com/api/gtdbrain/v1/mcp`, a
streamable-HTTP MCP server with OAuth 2.1 sign-in (dynamic client registration; the server card
is at [`/.well-known/mcp/server-card.json`](https://mcp.gtdbrain.com/.well-known/mcp/server-card.json)).
`GEMINI.md` holds the GTD instructions Gemini follows and `commands/gtd/*.toml` the slash
commands. Nothing else.

## License

MIT — see [LICENSE](./LICENSE). GTD® and Getting Things Done® are registered trademarks of
the David Allen Company; GTD Brain is not affiliated with or endorsed by it.
