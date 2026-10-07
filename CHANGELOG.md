# Changelog

Notable changes to the Faivelo plugin for Cursor, Claude Code and Gemini CLI.
The hosted MCP server itself ships with faivelo.com and is not versioned here.

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
