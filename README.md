# Faivelo Email MCP server

[![smithery badge](https://smithery.ai/badge/faivelo/mail)](https://smithery.ai/servers/faivelo/mail)

Give Claude, ChatGPT, Cursor or any MCP client a real email address on your own
domain. Read and send mail, search every mailbox, manage aliases and DNS: all
from the assistant you already use.

**Server URL:** `https://faivelo.com/api/mcp` (streamable HTTP, OAuth 2.1, no API key to paste)

**Access:** needs a Faivelo account. MCP is included on Growth and up, and in
the 14-day free trial (no card).

Registry name: `com.faivelo/mail`

## Connect

**Claude (claude.ai / Desktop):** Settings → Connectors → Add custom connector →
paste `https://faivelo.com/api/mcp` → sign in to Faivelo and approve.

**Claude Code:**

```bash
claude mcp add --transport http faivelo https://faivelo.com/api/mcp
```

**Cursor / VS Code / other clients:**

```json
{
  "mcpServers": {
    "faivelo": { "url": "https://faivelo.com/api/mcp" }
  }
}
```

The first call opens a browser sign-in, where you choose exactly which
mailboxes the assistant can reach.

## Tools

| Area | Tools |
|---|---|
| Mail | `list_messages`, `read_message`, `get_thread`, `search_messages`, `search_all_mailboxes`, `send_message`, `move_message`, `mark_spam`, `mark_all_read`, `delete_message`, `get_attachment`, `get_delivery_status`, `list_folders` |
| Mailboxes | `list_mailboxes`, `create_mailbox`, `get_account_summary`, `get_contacts` |
| Aliases | `list_aliases`, `create_alias`, `delete_alias` |
| Domains & DNS | `list_domains`, `list_dns_records`, `create_dns_record`, `update_dns_record`, `delete_dns_record` |

Every tool declares `readOnlyHint` / `destructiveHint`, so clients can ask
before anything that sends or deletes.

## Don't have email on your domain yet?

```bash
npx faivelo init yourdomain.com
```

Connects the domain, writes the DNS records (automatically on Vercel, Cloudflare,
Netlify and other supported hosts) and creates your mailboxes. Plans start at
$6/mo for unlimited mailboxes; forwarding is free.

- Website: https://faivelo.com/ai-agents
- Docs: https://faivelo.com/docs/developers/connect-claude/
- Node SDK: `npm install faivelo`
