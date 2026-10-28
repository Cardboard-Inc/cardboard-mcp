# Installing Cardboard

Cardboard is a hosted, remote MCP server. There is nothing to clone, build or run locally.

## Steps

1. Add the `cardboard` entry below to `mcpServers` in Cline's MCP settings file. Preserve existing server entries and
   settings. If Cardboard is already configured, update its entry instead of adding a duplicate.

```json
{
  "mcpServers": {
    "cardboard": {
      "type": "streamableHttp",
      "url": "https://mcp.cardboard.ai/mcp"
    }
  }
}
```

2. Save the settings and connect to Cardboard. It uses OAuth with dynamic client registration, so no API key, client ID
   or client secret needs to be supplied manually.
3. Let the user complete sign-in and consent in the browser. They sign in to their own Cardboard account and approve
   access. If they need an account, they can sign up at <https://www.cardboard.ai>.

## Check it works

After authorization, call `list_projects`. A successful response containing the user's projects, or an empty list for
a new account, confirms the connection. If authorization is incomplete or the call fails, report that the connection
still needs attention.

## Docs

<https://docs.cardboard.ai/mcp>
