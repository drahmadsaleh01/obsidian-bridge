# Obsidian Bridge Privacy Draft

Obsidian Bridge is designed to let an authorized user access an enrolled Obsidian vault through ChatGPT without uploading or mirroring the entire vault to a hosted cloud database.

## Data processed

The service may process note paths, note contents, metadata, search queries, command status, device identifiers, access scopes, timestamps, and limited operational logs necessary to route and audit authorized requests.

## Data location and transport

Vault content remains on the enrolled Obsidian device until an authorized tool call requests specific content or a requested write action is sent to the device. Requests and results are transported over HTTPS through the Obsidian Bridge backend.

## Authentication and security

Device credentials are scoped and revocable. Permanent raw device credentials are not intended to be stored in public source code. The ChatGPT app integration must use a user-safe authorization flow before production publication.

## Destructive actions

The initial public tool surface intentionally excludes delete and bulk-destructive operations.

## Retention

Operational command and audit records may be retained for reliability, security, debugging, and abuse prevention. A production retention period will be documented before public submission.

## User control

Users can revoke enrolled Obsidian devices. Production app authorization will also provide a way to revoke ChatGPT access.

## Contact

Support and privacy contact details will be added before public submission.
