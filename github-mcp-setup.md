# GitHub MCP Setup

Read the Exercise 1 user story ([Issue #1](https://github.com/Ankoul/drivecraft-exercise1-docs/issues/1)) through the GitHub MCP server.

## 1. Create a token

Create a classic token with **no scopes** ticked (public repositories only):
https://github.com/settings/tokens/new

Set a short expiration (for example 7 days) and copy the token. Never commit it to a repository.

## 2. Add the MCP config

Save as `.vscode/mcp.json` (use the `mcpServers` key if your client requires it):

```json
{
  "servers": {
    "github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/",
      "headers": {
        "Authorization": "Bearer ${input:github_token}"
      }
    }
  },
  "inputs": [
    {
      "id": "github_token",
      "type": "promptString",
      "description": "GitHub PAT (public repo read only)",
      "password": true
    }
  ]
}
```

Paste the token when prompted.

## 3. Verify

Ask your agent to read issue `1` from `Ankoul/drivecraft-exercise1-docs`.
