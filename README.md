# Roleford job search

Run your tech job search from your AI agent. Roleford matches you to engineering jobs every morning from your CV,
GitHub and what you're looking for. Your agent finds those matches, looks into the promising ones, unlocks the ones you
pick with your Roleford tokens, prepares your application if you want ours, and keeps your applications and
follow-ups up to date, without leaving the tool you already use.

This repository connects your agent (Claude Code, Claude, Codex, Cursor, Gemini CLI and others) to the Roleford MCP
server at `https://mcp.roleford.com/mcp`, and adds a `job-search` skill that walks it through the routine. It holds only configuration and
instructions: the server runs on Roleford. More on [roleford.com/mcp](https://roleford.com/mcp?utm_source=github&utm_campaign=plugin-readme).

## Before you start

Your agent works from your Roleford profile, so set it up on [roleford.com](https://roleford.com/?utm_source=github&utm_campaign=plugin-readme) first: add your
CV or connect GitHub, and approve what we found. Connecting is free. Unlocking a job (the company, the posting, where
to apply and who to write to) is 10 tokens, as on the website.

## How you connect

Add the server's URL to your agent, then sign in from it. Your agent opens roleford.com in your browser: sign in,
check what the agent will be able to do, choose how many jobs a day your agents may unlock (3 unless you change it),
and press **Allow**. Your agent keeps the access it gets and renews it by itself while you use it. Nobody copies a
token.

Each agent you connect is listed on roleford.com under **Profile → Your agents**, where you can disconnect it or change
the daily limit at any time.

## Install

One click, then confirm in your client and sign in on roleford.com when it asks:

- **Claude** (claude.ai and Claude Desktop): [Add Roleford to Claude](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Roleford&connectorUrl=https%3A%2F%2Fmcp.roleford.com%2Fmcp)
- **Cursor:** [![Add roleford MCP server to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en/install-mcp?name=roleford&config=eyJ1cmwiOiJodHRwczovL21jcC5yb2xlZm9yZC5jb20vbWNwIn0%3D)
- **VS Code:** [![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_Roleford-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://vscode.dev/redirect/mcp/install?name=roleford&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.roleford.com%2Fmcp%22%7D)

Each link opens the client's own add-server dialog with the URL filled in; nothing is added until you confirm it there.

### Claude Code

```bash
claude plugin marketplace add gitranks/roleford-job-search
claude plugin install roleford-job-search@roleford
```

Then run `/mcp`, pick `plugin:roleford-job-search:roleford`, choose **Authenticate** and sign in on roleford.com.

Without the plugin: `claude mcp add --scope user --transport http roleford https://mcp.roleford.com/mcp`, then `/mcp` → `roleford` →
**Authenticate**.

### Claude Desktop and claude.ai

Use the Add to Claude link above, or by hand: **Customize → Connectors → + Add → Add custom connector**, name
`Roleford`, URL `https://mcp.roleford.com/mcp`. Then **Connect** it and sign in on roleford.com. On a Team or Enterprise plan, an Owner adds
the connector and you press **Connect**.

### Gemini CLI

```bash
gemini extensions install https://github.com/gitranks/roleford-job-search
```

Then run `/mcp auth roleford` in Gemini CLI. Without the extension:
`gemini mcp add --scope user --transport http roleford https://mcp.roleford.com/mcp`.

### Codex

```bash
codex mcp add roleford --url https://mcp.roleford.com/mcp
codex mcp login roleford
```

### Cursor and VS Code

Use the links above, or add the server by hand. Cursor, in `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "roleford": { "url": "https://mcp.roleford.com/mcp" } } }
```

then press **Connect** beside `roleford` in Cursor's MCP settings. VS Code, from a macOS or Linux terminal:

```bash
code --add-mcp '{"name":"roleford","type":"http","url":"https://mcp.roleford.com/mcp"}'
```

### Other clients

Any client with remote MCP servers and sign-in (OAuth) works: add a streamable HTTP server named `roleford` at
`https://mcp.roleford.com/mcp` with no headers, and start its sign-in. Setup for self-installing agents: [llms-install.md](llms-install.md).

### Plugin formats in this repository

| File | For |
| --- | --- |
| `.claude-plugin/` | Claude Code plugin and marketplace |
| `gemini-extension.json` | Gemini CLI extension |
| `plugin.json`, `mcp.json`, `.agents/plugins/marketplace.json` | Agent Plugins format (Codex, Cursor, Copilot) |
| `.antigravity-plugin/`, `mcp_config.json` | Antigravity |
| `.devin-plugin/` | Devin |

## Use it

Ask your agent: "Run my job search for today with Roleford." It checks where you stand, shows today's new matches with
why they fit, and tells you which follow-ups are due. Ask it to look closer at a job, unlock it, prepare your
application, or log an interview.

In Claude Code the plugin adds two commands:
- `/roleford-job-search:today [skills, place or work mode]`: status, new matches worth a look, and follow-ups due;
- `/roleford-job-search:status`: your applications, where each one stands and what it needs from you.

## What is sent to Roleford

Everything goes to `mcp.roleford.com`, except the sign-in page, which is on `roleford.com`.

When you sign in:
- your agent registers itself: the name it gives itself, the address the sign-in answer goes back to (on your
  computer, or the client's own page), and the other details it registers with, such as its version or homepage. The
  consent page shows the name and the address;
- you sign in to roleford.com, choose the daily unlock limit and press Allow. Your agent then gets an access token and
  a refresh token from `mcp.roleford.com`. It sends the access token with every call and uses the refresh token to
  renew it.

With every tool call, the access token, and:
- the filters you ask `find_jobs` for, and the jobs you open, rate (with your reasons and note) or unlock;
- changes to what you're looking for: roles, places, work modes, levels, contracts, companies to never show and the
  expected salary;
- for an application: your edits to the tailored CV and email draft, the instructions for a rewrite, and what happened:
  applied (and who you emailed), the stage, interviews with their time and notes, and follow-ups.

Your agent, and the AI company behind it, receive what the tools answer: your profile, the jobs matched to you, the jobs
you unlock with the people at those companies we suggest writing to, and your applications. Roleford never sees your
other files, your mailbox or your model's API key. See the
[privacy policy](https://roleford.com/privacy?utm_source=github&utm_campaign=plugin-readme#agents) for what Roleford does with your data.

## License

MIT
