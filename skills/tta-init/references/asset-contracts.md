# Governance Asset Contracts

These contracts turn Matt-inspired ideas into project files without installing or copying the Matt Skills package.

## `AGENTS.md`

Must state:

- what the project is and where its important code/content lives;
- which files are authoritative and which are generated or local-only;
- how `temp/` is used and what must not be committed;
- the project's validation and delivery expectations;
- how an Agent should handle existing work and uncertainty.

Do not fill it with generic slogans or guessed commands.

## `CONTEXT.md`

Write verified facts, not a product pitch. Capture:

- the project's purpose and current boundaries;
- domain terms and their preferred meanings;
- important data, route, module, or integration relationships;
- hard constraints and known failure modes;
- links to durable decisions when they exist.

Unknown facts are marked as `待确认`, with the question needed to resolve them. Do not create a separate glossary for a small project when one clear section in `CONTEXT.md` is enough.

## ADR

Each durable decision records:

1. status and date;
2. context and the problem being decided;
3. decision;
4. consequences and trade-offs;
5. rejected alternatives when they matter.

An ADR is not a research dump or a speculative TODO list.

## `temp/reports/` and `temp/handoff/`

Research reports record the question, scope, sources, findings, uncertainty, and practical implications. Handoffs record the objective, current state, changed files, validation evidence, blockers, and the next safe action. Both are working materials and stay in `temp/` unless the user promotes them to durable project documentation.

## Issue and PR templates

Use them only when the project uses GitHub collaboration. Keep fields actionable: environment/version, expected and actual behavior, reproduction, evidence, scope, testing, and reviewer notes. Do not add templates merely to fill the tree.
