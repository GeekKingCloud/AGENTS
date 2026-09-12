# Security and Privacy Preferences

Use this file whenever work touches secrets, accounts, permissions, channels, public repos, logs, user data, or external services.

## Never commit or publish

- API keys, tokens, app passwords, OAuth state, private keys, cookies
- production `.env` files or live config with secrets
- user/channel IDs, allowlists, route IDs, or private contact lists unless explicitly intended and safe
- session logs, chat transcripts, local databases, memory stores, or tool traces
- private personal facts in public working documents or test fixtures

## Redaction and reporting

Owner-facing or public reports should summarize the issue without dumping raw secrets, local paths, tracebacks, config files, or IDs. Say that host-local logs can be inspected separately when needed.

## Permission boundaries

Use the current granted action set under the [root authority boundary](../AGENTS.md#local-and-remote-authority); access to a system is not itself permission to change it. Do not ask again for an already-authorized step within that scope. Seek approval before crossing an ungranted boundary, including:

- pushing commits, opening or updating pull requests, merging, publishing releases, deploying, or otherwise changing remote/public state
- rotating credentials or changing account security
- posting publicly or sending messages/emails to real people
- purchasing services or incurring unusual cost
- deleting data or running destructive commands
- changing production permissions, firewall rules, OAuth scopes, or deploy keys

Routine local administration and credentialed read-only lookups may be covered by an existing grant; neither privilege nor credential use alone demands renewed permission. Confirm that the grant covers the exact target and effects. New data exposure, production impact, account/security changes, destructive actions, cost, and public sends require approval when not already covered. Preserve explicit stop/approval gates and the [destructive-cleanup controls](../workflows/workspace-cleanup.md); a broad cleanup request is not blanket deletion authority.

## Public Artifacts and Fixtures

Use synthetic data for fixtures and demonstrations. Example domains, fake IDs, and placeholders should be obviously fake. Public working-preference repositories may describe personal taste, but must not contain private memory, host-specific secrets, session histories, or identifying operational data.

Bad:

```text
TELEGRAM_USER_ID=<real-user-id>
```

Good:

```text
TELEGRAM_USER_ID=0000000000  # synthetic example only
```

## Security review prompts

For risky changes, check:

- untrusted input into shell, SQL, paths, templates, eval, redirects, URLs, deserialization, or regexes
- auth/authz/session boundaries
- tenant/user data separation
- dependency and install-script risk
- logging and error messages
- default permissions and failure modes
