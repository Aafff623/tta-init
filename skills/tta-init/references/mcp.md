# Local MCP Policy

MCP configuration is runtime configuration, not a committed project asset in the TTA model.

## Scope and source

General-purpose MCP belongs in the user's global tool configuration. An MCP used only by one project belongs in that Project's local configuration. Both remain outside Git.

When the user confirms a project-level MCP requirement:

1. Keep the local project source at `.agents/mcp.json`.
2. Put server names, verified endpoints, transport choices, and environment-variable references there; never put secret values there.
3. Keep secret values and local credential backups in the user's approved local location or `temp/secrets/` when that is the project's explicit policy.
4. Ignore the MCP file in Git.
5. Configure a tool-native file only when the current tool documents that path and schema, and ignore the native file too.
6. Treat the native file as a generated or manually imported runtime view, never as a second source of truth.

The existence of `.agents/mcp.json` does not make other tools read it automatically. `tta-init` v1 does not provide a universal synchronizer. Do not write or recommend `tta mcp sync` unless a real executable has been implemented and verified in the current project.

## Git granularity

`.gitignore` works at file and directory level, not at JSON-property level. If a native tool file mixes ordinary project settings and MCP settings, do not pretend that only its MCP fields are ignored. Use a dedicated local MCP file when the tool supports one; otherwise treat the whole mixed file as local-only and keep any shareable non-MCP settings elsewhere.

## Secrets and temporary material

Keep secret values in the user's approved local secret location or in `temp/secrets/` when that is the project's explicit policy. Do not echo them, place them in logs, or write them to tracked files. `.gitignore` reduces accidental commits; it is not a backup or encryption system.

## Verification

The Skill may verify that a local JSON file parses and that a tool exposes the configured server only when the relevant tool is available. It must distinguish:

- configuration file exists;
- the tool exposes the server;
- an actual MCP call succeeds.

Do not report the first state as proof of the other two.
