# Connect to I Know Blockchain — Chia with native Codex

September 17, 2026: production login and a fresh Codex process passed. Access is currently allowlisted to Jake. Other accounts need an invitation before this connection will work. This is a remote MCP connection, not an executable plugin ZIP or an approved store listing.

## Windows setup

1. Install/sign in to Codex using its normal instructions. No Chia node, wallet software or private backend repository is required.
2. Merge the following entries into your Codex `config.toml` (normally `%USERPROFILE%\.codex\config.toml`). Preserve existing settings; do not duplicate an existing table. Put the top-level credentials-store setting before any table headers.

```toml
mcp_oauth_credentials_store = "keyring"

[mcp_servers.ikb-chia-production]
url = "https://chia.iknowblockchain.com/mcp"

[mcp_servers.ikb-chia-production.oauth]
client_id = "14C4VTRF1mLTq4Z2j2iyHmnHWvXKjQHG"
callback_port = 8765
```

3. In PowerShell run `codex mcp login ikb-chia-production --scopes chia:read,offline_access`. Follow the browser link, choose the invited Google account and accept read-only/offline access. Credentials are stored in Windows Credential Manager. Never paste a token into chat.
4. Start a fresh Codex session and ask: “Use Chia to convert 0.25 XCH to mojos, explain a mojo and link the source.” Expected conversion: `250000000000` mojos.
5. For news ask for publication dates and source links. For public address lookups, specify mainnet or Testnet11; results cover one address, not every address in a wallet. Never provide a seed phrase or private key.

The verified native callback is `http://127.0.0.1:8765/callback/X6_7--Ft5FfG`. If another Codex version/device emits a different callback, stop and contact support with that callback URL only (not the full authorization URL). The operator registers exact callbacks; no wildcard is used. Other host applications have separate registration requirements. Explicit oauth_resource is omitted because this tested client uses protected-resource discovery.

To disconnect, use `codex mcp logout ikb-chia-production` and remove only this server's config tables. Local logout removes the local credential; request account/service revocation separately if needed.

## Troubleshooting

- `invitation_required` / 403 after sign-in: account is not enrolled. Contact support; signing in alone does not grant access.
- 401: sign in again; a wrong audience, expired or invalid token is rejected.
- 429: retry after the indicated delay. 503: service unavailable, not zero holdings.
- If the browser appears stuck on consent, check the terminal's result before repeatedly submitting. During our release test the page remained visible after native login had succeeded.

Support: support@iknowblockchain.com. Feedback: feedback@iknowblockchain.com. Include host/version, OS, approximate time and prompt; omit authorization URLs, tokens and private wallet information. Windows Native Codex is the verified OAuth path; consumer ChatGPT, Claude and other hosts are not claimed tested here.

Publisher: ZTOR Services Incorporated, Kansas, USA.

[Website](https://iknowblockchain.com/) · [Privacy](https://iknowblockchain.com/privacy/) · [Terms](https://iknowblockchain.com/terms/) · [Help](https://iknowblockchain.com/support/)

Release candidate: invite-only Native Codex connection. Backend source and credentials are not distributed. Not a vendor-approved listing. Apache-2.0 applies to original release materials; third-party sources and marks retain their rights.
