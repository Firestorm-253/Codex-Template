# AGENTS.md

This file defines the global rules Codex must follow in this repository.

## Execution scope

This repository is a filtered Codex execution workspace.

The full product roadmap, developer planning, and non-actionable project context are intentionally outside this repository.

Codex receives actionable work only through `.codex/CURRENT_TASK.md`.

Codex must not infer additional tasks from missing features, incomplete architecture, milestone context, filenames, TODOs, or memory files.

When the current task is complete, Codex must stop and report completion.

## Required read order

Before planning or editing, read these files in order:

1. `.codex/INDEX.md`
2. `.codex/CURRENT_TASK.md`
3. `.codex/TDD_CONTRACT.md`
4. `.codex/CURRENT_MILESTONE.md`
5. `.codex/WORKFLOW.md`
6. `.codex/memory/INDEX.md`
7. `.codex/memory/project_state.md`
8. Any additional files explicitly referenced by the current task

Do not scan unrelated files to gather extra context. Pull in additional files only when they are needed for the current task.

## File authority

`AGENTS.md` and Markdown files with ALL_CAPS names are owner-authored contract files.

Codex may read contract files, but must not edit, rename, delete, rewrite, summarize over, or regenerate them unless the user explicitly asks for that exact file to be changed.

Lowercase Markdown files are mutable memory files. Codex may update them only when the current task changes the facts they describe.

## Root boundary

Treat this directory as the project root.

Do not read from or write to paths outside this root.

If a task appears to require outside files, stop and report the missing dependency instead of guessing.

## Task boundary

Only implement the task described in `.codex/CURRENT_TASK.md`.

`.codex/CURRENT_MILESTONE.md` provides context and constraints. It is not permission to implement the whole milestone.

If `.codex/CURRENT_TASK.md` has `Task status: NOT SET`, do not modify code. Report that no active task is configured.

## TDD requirement

All code behavior changes must follow `.codex/TDD_CONTRACT.md`.

Documentation-only tasks may skip the red/green loop only under the conditions defined in `.codex/TDD_CONTRACT.md`.

## Memory requirement

At the end of a completed task, update mutable memory files according to `.codex/memory/INDEX.md`.

Do not add speculation to memory files.

## Workflow requirement

Run each task according to `.codex/WORKFLOW.md`.
