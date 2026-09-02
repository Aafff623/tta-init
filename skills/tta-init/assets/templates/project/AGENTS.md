# {{PROJECT_NAME}} Agent Rules

## Project purpose

{{PROJECT_SUMMARY}}

## Read first

- `README.md` for startup and daily usage.
- `CONTEXT.md` for verified domain facts and shared terminology.
- `temp/AGENTS.md` before entering or creating files under `temp/`.
- `.agents/skills/` when a task matches a project-specific Skill.

## File boundaries

- Product code and durable project documentation belong in their normal project locations.
- Temporary scripts, raw input, research, previews, reports, logs, handoffs, caches, and local secrets belong under `temp/`.
- `temp/` payloads and MCP configuration are local-only. Do not commit them.
- `.agents/skills/` contains project Skills and is tracked when it has real content.

## Working rules

- Inspect the current project and Git status before editing.
- Preserve unrelated changes and existing user-authored rules.
- Do not invent commands, paths, endpoints, or domain facts. Mark uncertainty for confirmation.
- Use Superpowers for the implementation workflow when it is available: clarify, plan, implement, test, review, and verify.
- Do not copy an external Skill package into this project just to make the tree look complete.

## Completion

Report the files changed, checks run, remaining uncertainty, and any work intentionally left for the user. Do not claim deployment, MCP health, or production acceptance without direct evidence.
