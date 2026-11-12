# Installing Roleford job search (for AI agents)

1. Add a remote MCP server named `roleford`:
   - transport: streamable HTTP
   - URL: `https://mcp.roleford.com/mcp`
   - no headers.
2. Connect it. The server answers the first call with a sign-in request: start your client's sign-in (OAuth) for
   `roleford`. It opens roleford.com in the user's browser, where they sign in, choose how many jobs a day agents may
   unlock, and press Allow. Tell the user that is what the page is for. Never ask them to paste anything from it.
3. Check the connection by calling `get_status`. A 401 after sign-in means the user cancelled or disconnected the agent
   on roleford.com: sign in again.
4. Read `skills/job-search/SKILL.md` for the routine: status, find, preview, unlock with the user's tokens, apply,
   track.
