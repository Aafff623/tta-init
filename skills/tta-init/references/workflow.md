# TTA Init Workflow

This reference defines the interaction contract for initialization. It is intentionally smaller than a project-management framework.

## Phase 1: discover the project

Before creating files, inspect:

- the requested path and its immediate contents, including hidden files;
- the real Git root and current status when Git is present;
- applicable `AGENTS.md` and `CLAUDE.md` files;
- existing `README.md`, `CONTEXT.md`, `.gitignore`, `.agents/skills/`, and tool configuration;
- whether the directory is empty, an existing project, or a project with unrelated uncommitted work.

Never infer that an empty-looking directory is safe to overwrite until hidden files and Git state are checked.

## Phase 2: short confirmation rounds

Ask only decisions that change the file tree.

### Round A: project boundary

Use one Project root. The old Workspace + Project mode is not an option. Ask only if the requested path or project root is ambiguous.

### Round B: governance profile

Offer:

- **MVP:** `README.md`, `AGENTS.md`, `CLAUDE.md`, `CONTEXT.md`, `.gitignore`, and `temp/` entry rules;
- **MVP + GitHub:** MVP plus Issue and PR templates;
- **MVP + ADR:** MVP plus an ADR template, creating actual ADR files only when decisions exist;
- **Custom:** the user selects individual optional modules.

Do not install Matt Pocock's Skills. Use its useful engineering ideas as independently written templates.

### Round C: local integrations

Ask whether the project has a project-level MCP requirement, which real servers are needed, and which tools are actually used. Do not create an empty MCP file, guessed native configuration paths, or placeholder servers. MCP files are local-only and ignored. Skills remain tracked.

## Phase 3: safe rendering

For a new empty project, render the templates in `assets/templates/project/` and replace every `{{TOKEN}}` with verified values. For an existing project:

- never replace an existing governance file wholesale;
- preserve unrelated edits and local terminology;
- add only missing files or sections;
- report conflicts instead of silently choosing between competing rules.

Create temporary subdirectories on demand. Do not add empty `docs/`, `assets/`, `.github/`, or ADR directories merely to make the tree look complete.

## Phase 4: verification

Verify the observable result:

- all required entry files exist and contain project-specific content;
- `temp/` payloads and local MCP files are ignored while `temp/README.md`, `temp/AGENTS.md`, and `.agents/skills/` remain available as intended;
- any MCP JSON written locally parses successfully;
- no secrets, tokens, cookies, private keys, or machine-specific credentials were written to tracked files;
- no unrelated files changed;
- the final report distinguishes created, skipped, preserved, and unverified items.
