# GitHub MCP Setup (IntelliJ and Copilot CLI)

Read the Exercise 1 user story ([Issue #1](https://github.com/Ankoul/drivecraft-exercise1-docs/issues/1)) through the GitHub MCP server.

## 1. Create a token

Create a classic token with **no scopes** ticked (public repositories only):
https://github.com/settings/tokens/new

Set a short expiration (for example 7 days) and copy the token. Never commit it to a repository.

## 2. Expose the token as an environment variable

```powershell
Add-Content $PROFILE '$env:GITHUB_PUBLIC_PAT = "your-github-token"'
```

Open a new terminal (and restart IntelliJ) afterwards so the variable is loaded.

## 3. Add the MCP config

| | IntelliJ | Copilot CLI |
|---|---|---|
| Manage | `Settings \| Tools \| GitHub Copilot \| Model Context Protocol (MCP)` | `/mcp` |
| Config file | `~/AppData/Local/github-copilot/intellij/mcp.json` | `~/.copilot/mcp-config.json` |
| Config file field | `servers` | `mcpServers` |

<details>
<summary>IntelliJ (click to expand)</summary>

```json
{
  "servers": {
    "public-github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/",
      "headers": {
        "Authorization": "Bearer ${GITHUB_PUBLIC_PAT}"
      }
    }
  }
}
```

</details>

<details>
<summary>Copilot CLI (click to expand)</summary>

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

</details>

## 4. Verify

- **IntelliJ:** open the MCP settings page and check that `public-github` is running.
- **Copilot CLI:** run `/mcp` and check that `public-github` is connected.

Then ask the agent to read issue `1` from `Ankoul/drivecraft-exercise1-docs`.
