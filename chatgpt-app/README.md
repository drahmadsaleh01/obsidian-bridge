# Obsidian Bridge — ChatGPT App

Status: integration scaffold in progress.

## Goal

Let an authorized ChatGPT user read and manage an enrolled Obsidian vault through the existing Obsidian Bridge without mirroring the vault to the cloud.

## Primary archetype

Submission-ready connector-style ChatGPT app backed by MCP.

## Existing production bridge

- MCP endpoint: `https://uzrrqsyhbagkxgdgegft.supabase.co/functions/v1/obsidian-bridge/mcp`
- Device transport: outbound HTTPS from Obsidian to Supabase Edge Functions.
- The vault remains on the enrolled Obsidian device.
- Device access is scope-based and revocable.

## Tool surface

Read-only:
- `search_notes`
- `read_note`
- `operation_status`

Mutating:
- `create_note`
- `update_note`
- `move_note`
- `set_property`

Policy target:
- Read-only tools may run without repeated confirmation after the app is connected.
- Mutating tools should be marked as write actions and remain reviewable/confirmable in ChatGPT.
- No delete or bulk destructive action in v1.

## Security model

1. Obsidian devices enroll through the existing one-time device-code flow.
2. Device tokens are stored locally on the enrolled device; server-side device records store token hashes.
3. ChatGPT must authenticate as an app client before MCP calls can reach the vault.
4. The MCP server must never expose a permanent client secret in public source or browser code.
5. Write actions require least-privilege scopes and explicit action metadata.

## Remaining work before ChatGPT publication

1. Make the MCP endpoint fully Apps SDK / current MCP compatible, including tool annotations.
2. Add a user-safe authentication flow for ChatGPT (OAuth-compatible rather than a pasted permanent bearer token).
3. Add app metadata, support/privacy URLs, and production-domain checks.
4. Validate read and write calls end-to-end against an enrolled iPhone vault.
5. Test in ChatGPT Developer Mode on web where eligible.
6. Submit the app for directory review so it can become available on supported ChatGPT surfaces, including mobile when approved/supported.

## Important product limitation

Private/custom MCP apps are currently a web-only testing path in ChatGPT. Native iPhone use therefore depends on the app being distributed through the supported ChatGPT plugin/app path rather than relying only on a private MCP connection.
