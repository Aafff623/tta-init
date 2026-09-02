---
name: tta-init
description: Use when initializing or re-initializing a single project for AI-assisted development, especially when it needs minimal agent rules, project Skills, a controlled temp workspace, local-only MCP setup, or optional GitHub issue and PR templates.
metadata:
  short-description: Initialize a minimal AI-assisted project
---

# TTA Init

Initialize one project without turning it into a framework or overwriting work that already exists.

## Core contract

- Treat the selected directory as the only Project root. Do not create or revive a Workspace + Project hierarchy.
- On Windows, prefer the user's D: drive project location and preserve an explicitly selected path; never move a project merely to satisfy this convention.
- Inspect before editing: locate the real project root, read applicable rules, check Git status, and inventory existing entry files and Skills.
- Preserve existing work. In a non-empty project, add only missing pieces or make narrowly scoped changes explicitly justified by the user's choices. Never replace an existing `AGENTS.md`, `CLAUDE.md`, `README.md`, or `.gitignore` wholesale.
- Create useful content, not empty governance shells. Do not create optional directories until the project has a reason and content for them.
- Use Superpowers for the coding workflow. Do not copy its package into the project and do not invent a second implementation/TDD/review workflow here.
- Do not install Matt Pocock's Skills. Adapt only the selected governance ideas into the project templates: shared context, durable decisions, clear issue boundaries, and handoff quality.
- Project Skills are tracked project assets. MCP configuration, secrets, and temporary payloads are local-only and must be ignored by Git.
- Never claim that a command, synchronizer, plugin, or tool automatically exists unless it was found in the current project or verified in the current environment. In particular, do not document `tta mcp sync` unless this command has actually been implemented.

## Use this skill when

- a user asks to initialize, bootstrap, standardize, or re-initialize an AI-assisted project;
- a new project needs `AGENTS.md`, `CLAUDE.md`, `README.md`, `CONTEXT.md`, Skills, or `temp/` rules;
- several coding agents will work on the same project and local MCP configuration must be kept separate from committed assets;
- the user wants optional Issue/PR templates or durable architecture-decision templates.

Do not use it for ordinary feature work, general MCP troubleshooting, or a broad repository cleanup unless initialization is part of the request.

## Fixed project model

The default MVP creates or verifies:

| Asset | Rule |
|---|---|
| `README.md` | Human-facing project start and run instructions |
| `AGENTS.md` | Shared project rules and agent boundaries |
| `CLAUDE.md` | Thin Claude Code entry that points to the shared rules |
| `CONTEXT.md` | Verified domain facts, vocabulary, and hard constraints |
| `.gitignore` | Ignores `temp/` payloads and local MCP files without hiding source Skills |
| `temp/` | Local input, research, scripts, reports, handoff, logs, cache, preview, and secrets workspace |
| `.agents/skills/` | Project-specific Skills, if the project has any; track their real content |

Matt-derived `CONTEXT.md`, ADR, issue, and handoff ideas are templates and writing contracts, not a dependency. Superpowers remains the implementation workflow.

## Workflow

1. **Discover.** Confirm the requested directory, real Git root if any, current status, existing rules, existing Skills, and whether the directory is empty. Read [references/workflow.md](references/workflow.md).
2. **Confirm choices.** Use two or three short rounds only when decisions materially change the output: project mode, governance profile, and optional GitHub/assets modules. Do not ask about details that can be safely inferred.
3. **Build the MVP.** Render the templates in `assets/templates/project/` with verified project facts. For existing files, merge only missing sections after inspecting them; preserve the user's wording and local conventions.
4. **Apply optional modules.** Add `docs/adr/` only when durable architecture decisions exist or the user selects it. Add `.github/` templates only when the project uses GitHub issues or pull requests. Keep research reports and handoffs in `temp/`.
5. **Handle MCP locally.** If the user confirms project-level MCP and provides a real server configuration, create `.agents/mcp.json` as the local source and ignore it. Do not create an empty MCP shell or invent a server. Configure native tool files only when their current format and location are verified. Read [references/mcp.md](references/mcp.md). Do not promise automatic cross-tool synchronization without a real adapter.
6. **Verify.** Check unresolved template tokens, Markdown paths, JSON syntax for any local MCP file, Git ignore behavior, and the final `git status`. Report what was created, what was skipped, and any unverified tool integration.

## Asset quality gate

Every generated governance file must contain project-specific facts or an explicit, useful operating contract. If a fact is unknown, mark it for confirmation instead of inventing it. Use the contracts in [references/asset-contracts.md](references/asset-contracts.md).

Stop after initialization. Do not commit, push, install unrelated packages, clean temporary files, or rewrite history unless the user separately authorizes that action.
