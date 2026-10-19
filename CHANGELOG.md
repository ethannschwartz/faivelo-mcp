# Changelog

Notable changes to the Faivelo plugin for Cursor, Claude Code and Gemini CLI.
The hosted MCP server itself ships with faivelo.com and is not versioned here.

## 1.2.0

- New tool `get_domain_setup`: one domain's DNS records grouped as MX, SPF,
  DKIM, DMARC, sending and mail-app setup, each found or missing, with the
  exact record to add. Read-only; it never changes DNS.
- Read-only tools now state `destructiveHint: false` explicitly.

## 1.1.0

- New tool `update_mailbox`: set or clear the name a mailbox sends as.
- `send_message` and `send_batch` take `from` as `"Name <address>"` and an
  optional `fromName` for a one-message name; drafts take `fromName`.
- `list_mailboxes` returns each mailbox's `displayName`; a send with no name
  anywhere returns a `hint`.
- Skill: recommends `displayName` on `create_mailbox`.

## 1.0.0

- Cursor plugin: `.cursor-plugin/plugin.json`, `mcp.json` (the hosted server
  over OAuth, no key to paste), the `faivelo-email` skill and a Cursor rule
  generated from it, and the Faivelo mark as `assets/logo.svg`.
- Claude Code plugin and marketplace (`.claude-plugin/`, `.mcp.json`).
- Gemini CLI extension (`gemini-extension.json`, `GEMINI.md`).
- `faivelo-email` Agent Skill: set up email on a domain with `npx faivelo init`,
  send from an app with the SDKs or REST, verify inbound webhooks, use the
  MCP server.
- `server.json` for the official MCP Registry (`com.faivelo/mail`).
