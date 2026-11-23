# Changelog

Notable changes to the Faivelo plugin for Cursor, Claude Code and Gemini CLI.
The hosted MCP server itself ships with faivelo.com and is not versioned here.

## 1.3.1

Documentation corrections; no tool changed.

- `get_thread`, `label_message` and the `label` filter on `list_messages`
  work on agent inboxes only. A person's mailbox gets 403
  `agent_inbox_only`. Drafts work on every mailbox.
- The DNS record tools come with an API key only; a browser sign-in never
  gets them. Plugin descriptions now say "check a domain's DNS records".
- Drive tools appear on a browser sign-in only when the client asks for the
  `drive:read` scope.
- `create_mailbox`: 10 a day per key, 20 on the Developer plan, 100 on Scale.
- Plan access: Growth, Pro and Business, paid Agents plans, the free trial,
  and keys bound to a free agent address.
- Tool counts corrected, and the hosted-service tools (API key only) are
  listed in the README and the skill.
- Skill: correct scope list and limits; the generated Cursor rule no longer
  has a broken link to `references/mcp.md`.

## 1.3.0

- New tool `forward_message`: forward a received message to new recipients
  with an optional note, the original's headers and body, and its
  attachments (up to 10 MB). The subject becomes `Fwd: …` and the original
  keeps its read state. Same send limits as `send_message`.

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
