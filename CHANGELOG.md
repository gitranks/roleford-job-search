# Changelog

## Unreleased

## 0.1.3 (2026-11-17)

- Listing text only: a 29-character short description ("Job search from your AI agent") where the OpenAI and
  Devin manifests ask for one, a new long description, and the keywords `resume`, `software-engineer-jobs` and
  `remote-jobs`. Nothing the plugin does changes.

## 0.1.2 (2026-11-16)

- The `job-search` skill passes on what the matches are based on (`matchingOn`) and, when where the user
  lives or their level is missing, what the list shows and where to set it.

## 0.1.1 (2026-11-15)

- The `job-search` skill relays the out-of-tokens answer's `ways` instead of always offering a plan or a pack, which
  roleford.com doesn't sell yet.

## 0.1.0 (2026-11-12)

- The `roleford` MCP server (`https://mcp.roleford.com/mcp`, sign-in on roleford.com) for Claude Code, Gemini CLI,
  Codex, Cursor and Devin, and Antigravity (its sign-in not tested yet).
- The `job-search` skill, and the Claude Code commands `/roleford-job-search:today` and `/roleford-job-search:status`.
