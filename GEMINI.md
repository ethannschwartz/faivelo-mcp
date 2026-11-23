# Faivelo

The `faivelo` MCP server reads, searches, sends and organises mail in the
user's Faivelo mailboxes, manages aliases and checks a domain's DNS records.
The first call opens a browser sign-in where the user picks which mailboxes
you may use, and whether you may create new ones. To edit DNS records too,
connect with a Faivelo API key.

Ask the user before sending mail or deleting anything for them.

For setting up email on a domain (`npx faivelo init`), sending from an app
(SDK / REST) and receiving inbound mail as webhooks, follow the
`faivelo-email` skill in `skills/faivelo-email/SKILL.md`.
