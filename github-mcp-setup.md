# GitHub MCP Setup (IntelliJ and Copilot CLI)

Read the Exercise 1 user story ([Issue #1](https://github.com/Ankoul/drivecraft-exercise1-docs/issues/1)) through the GitHub MCP server.

## 1. Create a token

Create a classic token with **no scopes** ticked (public repositories only):
https://github.com/settings/tokens/new

Set a short expiration (for example 7 days) and copy the token. Never commit it to a repository.

## 2. Add the MCP config

| | IntelliJ | Copilot CLI |
|---|---|---|
| Manage | `Settings \| Tools \| GitHub Copilot \| Model Context Protocol (MCP)` | `/mcp` |
| Config file | `~/AppData/Local/github-copilot/intellij/mcp.json` | `~/.copilot/mcp-config.json` |
| Config file field | `servers` | `mcpServers` |
| Token | Prompted via `inputs` | Environment variable `GITHUB_PUBLIC_PAT` |

<details>
<summary>IntelliJ (click to expand)</summary>

```json
{
  "inputs": [
    {
      "id": "github_token",
      "type": "promptString",
      "description": "GitHub PAT (public repo read only)",
      "password": true
    }
  ],
  "servers": {
    "public-github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/",
      "headers": {
        "Authorization": "Bearer ${input:github_token}"
      }
    }
  }
}
```

Paste the token when prompted.

> Tip: to open the MCP settings (and the token prompt), press `Shift` twice and type `Settings | GitHub Copilot | Model Context Protocol (MCP)`.

</details>

<details>
<summary>Copilot CLI (click to expand)</summary>

Expose the token as an environment variable, then open a new terminal:

```powershell
Add-Content $PROFILE '$env:GITHUB_PUBLIC_PAT = "your-github-token"'
```

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

## 3. Verify

- **IntelliJ:** open the MCP settings page and check that `public-github` is running.
- **Copilot CLI:** run `/mcp` and check that `public-github` is connected.

Then ask the agent to read issue `1` from `Ankoul/drivecraft-exercise1-docs`.
