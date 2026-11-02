# GitHub MCP Setup (Copilot CLI)

Read the Exercise 1 user story ([Issue #1](https://github.com/Ankoul/drivecraft-exercise1-docs/issues/1)) through the GitHub MCP server.

## 1. Create a token

Create a classic token with **no scopes** ticked (public repositories only):
https://github.com/settings/tokens/new

Set a short expiration (for example 7 days) and copy the token. Never commit it to a repository.

## 2. Expose the token as an environment variable

```powershell
Add-Content $PROFILE '$env:GITHUB_PUBLIC_PAT = "your-github-token"'
```

Open a new terminal afterwards so the variable is loaded.

## 3. Add the MCP config

Add the `public-github` server to `~/.copilot/mcp-config.json`:

```json
{
  "mcpServers": {
    "public-github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/",
      "headers": {
        "Authorization": "Bearer ${GITHUB_PUBLIC_PAT}"
      },
      "tools": ["*"]
    }
  }
}
```

## 4. Verify

Start `copilot`, run `/mcp` to confirm `public-github` is connected, then ask it to read issue `1` from `Ankoul/drivecraft-exercise1-docs`.
