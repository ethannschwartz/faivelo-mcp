# Faivelo Email MCP server

[![smithery badge](https://smithery.ai/badge/faivelo/mail)](https://smithery.ai/servers/faivelo/mail)
[![Add to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/install-mcp?name=faivelo&config=eyJ1cmwiOiJodHRwczovL2ZhaXZlbG8uY29tL2FwaS9tY3AifQ%3D%3D)

Give Claude, ChatGPT, Cursor, Codex or any AI agent a real email inbox on
your own domain. Your assistant can read and search your mail, draft and
send replies, schedule sends, file messages away, create new addresses for
itself, and fix your domain's DNS. You choose exactly which mailboxes it can
see.

Useful when you want to:

- let your coding agent set up `hello@yourcompany.com` for the site it just built
- give an AI agent its own address to sign up for services and receive verification codes
- triage, summarise and answer a support inbox from Claude
- send a reply from your real address without opening a mail app

**Server URL:** `https://faivelo.com/api/mcp` (streamable HTTP, OAuth 2.1, no API key to paste)
**Registry name:** `com.faivelo/mail`
**Access:** a Faivelo account. MCP is included on Growth and up, and in the
free trial (no card). [Plans](https://faivelo.com/docs/billing/plans/?via=mcp)

## Install

| Client | One command |
| --- | --- |
| Claude Code (plugin: MCP + skill) | `/plugin marketplace add ethannschwartz/faivelo-mcp` then `/plugin install faivelo@faivelo` |
| Claude Code (MCP only) | `claude mcp add --transport http faivelo https://faivelo.com/api/mcp` |
| claude.ai / Claude Desktop | Settings → Connectors → Add custom connector → paste `https://faivelo.com/api/mcp` |
| Cursor | [Add to Cursor](https://cursor.com/install-mcp?name=faivelo&config=eyJ1cmwiOiJodHRwczovL2ZhaXZlbG8uY29tL2FwaS9tY3AifQ%3D%3D) |
| VS Code | [Install in VS Code](https://insiders.vscode.dev/redirect/mcp/install?name=faivelo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Ffaivelo.com%2Fapi%2Fmcp%22%7D) |
| Codex | `codex mcp add faivelo --url https://faivelo.com/api/mcp` |
| Gemini CLI | `gemini extensions install https://github.com/ethannschwartz/faivelo-mcp` |
| Windsurf | `{ "mcpServers": { "faivelo": { "serverUrl": "https://faivelo.com/api/mcp" } } }` in `mcp_config.json` |
| Any Agent Skills client | `npx skills add ethannschwartz/faivelo-mcp` (the `faivelo-email` skill) |
| Other clients | `{ "mcpServers": { "faivelo": { "url": "https://faivelo.com/api/mcp" } } }` |

The first call opens a browser sign-in, where you choose exactly which
mailboxes the assistant can reach.

**Headless agents** (no browser): send an API key instead,
`Authorization: Bearer fvl_live_...`. Create an *agent* key at
[Settings → Developers](https://faivelo.com/settings/developers?via=mcp); it
only reaches the mailboxes it creates or is granted.

## Tools

| Area | Tools |
| --- | --- |
| Reading | `list_messages`, `read_message`, `get_thread`, `search_messages`, `search_all_mailboxes`, `list_folders`, `get_attachment`, `get_contacts` |
| Sending | `send_message`, `create_draft`, `update_draft`, `send_draft`, `list_scheduled`, `cancel_scheduled`, `get_delivery_status` |
| Organising | `flag_message`, `label_message`, `move_message`, `restore_message`, `mark_spam`, `mark_all_read`, `delete_message`, `empty_trash` |
| Account | `list_mailboxes`, `create_mailbox`, `get_account_summary`, `get_setup_summary`, `list_aliases`, `create_alias`, `delete_alias` |
| Domains & DNS | `list_domains`, `list_dns_records`, `create_dns_record`, `update_dns_record`, `delete_dns_record` |
| Drive | `drive_list_files`, `drive_download_file` |

`get_setup_summary` returns a shareable markdown summary of what is set up
(domains, DNS state, mailboxes, what is still pending), for an agent to hand
to its human when it finishes.

Every tool declares `readOnlyHint` / `destructiveHint`, so clients can ask
before anything that sends or deletes.

## What's in this repo

- `server.json`: the official MCP Registry entry
- `.claude-plugin/` + `.mcp.json`: the Claude Code plugin and its marketplace
- `skills/faivelo-email/`: an [Agent Skill](https://agentskills.io) that teaches an agent to set up email on a domain, send from an app and verify inbound webhooks
- `gemini-extension.json` + `GEMINI.md`: the Gemini CLI extension

## Don't have email on your domain yet?

```bash
npx faivelo init yourdomain.com
```

Connects the domain, writes the DNS records (automatically on Vercel,
Cloudflare, Netlify and other supported hosts) and creates your mailboxes.
Plans start at $6/mo for unlimited mailboxes; forwarding is free.

- Website: https://faivelo.com/ai-agents?via=mcp
- Docs: https://faivelo.com/docs/developers/connect-claude/?via=mcp
- Node SDK: `npm install faivelo` · Python SDK: `pip install faivelo`
