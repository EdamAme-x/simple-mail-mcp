# Privacy policy

Effective date: October 1, 2026

This policy describes how the open-source `simple-mail-mcp` application (Mail MCP) handles information. Mail MCP runs on your computer and connects your mail providers to an MCP client you choose. It is not a hosted mailbox service operated by the project maintainers.

## Information accessed and its purpose

Mail MCP uses the accounts you register to search, list, and read email at the request of your MCP client. Depending on the request and provider, it processes account identifiers, search queries, message identifiers, sender and recipient details, subjects, dates, message text and HTML, and attachment metadata. IMAP message retrieval can also process attachment content in memory.

Gmail authorization requests the `gmail.readonly` scope. Outlook authorization requests `Mail.Read` and `offline_access`. IMAP connections use TLS and open mailboxes read-only. Mail MCP exposes no tools to send email, delete messages, or mark messages as read. An IMAP app password may permit additional operations at the provider even though Mail MCP does not expose them.

OAuth tokens allow Mail MCP to access a registered account and refresh access without asking you to sign in for every request. IMAP accounts use the credentials or app password you provide.

## Storage and retention

Mail MCP stores account configuration and credentials as unencrypted JSON files in `~/.mail-mcp/accounts/`. Older installations may also have a legacy `~/.mail-mcp/tokens.json` file. OAuth client credentials you supply may be stored separately on your computer. These files can contain access tokens, refresh tokens, client secrets, or IMAP passwords. POSIX permissions restrict access to credential files; Windows relies on your user profile's access controls.

Mail MCP processes message results in memory and does not maintain a persistent mailbox cache. Your operating system, backups, terminal logs, and MCP client can have separate retention behavior. Protect your computer and avoid sharing credential files or logs containing private information.

## Where information goes

Mail MCP sends authentication information and mail requests, including search queries when applicable, to the mail provider for the selected account. It returns requested mail information to the connected MCP client. That client may send information to an AI service or store conversation history according to its own settings and privacy policy. Review those settings before connecting private mailboxes.

The application does not include a maintainer-operated service for collecting mailbox contents or usage analytics. Mail data is used to provide the mail-reading and search functions requested through the MCP client, not sold or used by this application for advertising. This policy does not govern the independent practices of mail providers, MCP clients, AI services, or modified versions of the software.

The local HTTP server binds to `127.0.0.1` and checks Host and Origin headers, but has no remote authentication. Other processes on your computer may access its endpoint and registered accounts. Do not expose it through a public proxy.

## Disconnecting an account

Run `mail-mcp logout --account <name>` to remove the selected account's local credentials. Revoke OAuth access or the app password in your mail provider's settings to invalidate the provider authorization. Removing local credentials does not delete provider messages, backups, or copies retained by your MCP client or AI service. Manage those copies through the relevant service or application.

## Changes and contact

Updates to this policy are published in this repository with a revised effective date. For privacy questions, [open an issue](https://github.com/EdamAme-x/simple-mail-mcp/issues) using only non-sensitive information, or ask there for a private contact channel. Never post credentials or private email content in public issues. For vulnerabilities, follow the [security policy](SECURITY.md).
