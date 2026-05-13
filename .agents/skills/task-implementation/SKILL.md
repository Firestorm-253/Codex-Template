---
name: task-implementation
description: Use only for roadmap-driven work where the user explicitly invokes this skill, asks to use the current task, or asks to plan/implement the task from .codex/CURRENT_TASK.md. Do not use for unrelated repository tasks.
---

# Task Implementation Skill

This skill defines the rules you must follow during task implementation/planning.

Use the repository as a filtered execution workspace. The full product roadmap, developer planning, and non-actionable project context are outside this repository.

Actionable work comes from `.codex/CURRENT_TASK.md` and, when present, from the latest approved plan in the current conversation. Do not infer additional tasks from missing features, incomplete architecture, milestone context, filenames, TODOs, memory files, or adjacent code.

When the current task is complete, stop and report completion. Do not continue to another roadmap item.

## File authority

Markdown files with ALL_CAPS names are owner-authored contract files.

You may read contract files, but must not edit, rename, delete, rewrite, summarize over, or regenerate them unless the user explicitly asks for that exact file to be changed.

Lowercase Markdown files are mutable memory files. You may update them only when the current task changes the facts they describe.

## Root boundary

Treat this directory as the project root.

Do not read from or write to paths outside this root.

If a task appears to require outside files, stop and report the missing dependency instead of guessing.

## Task boundary

Only implement the task described in `.codex/CURRENT_TASK.md`.

`.codex/CURRENT_MILESTONE.md` provides context and constraints. It is not permission to implement the whole milestone.

## TDD requirement

All code behavior changes must follow `.codex/TDD_CONTRACT.md`.

Documentation-only tasks may skip the red/green loop only under the conditions defined in `.codex/TDD_CONTRACT.md`.

## Memory requirement

At the end of a completed task, update mutable memory files according to `.codex/memory/INDEX.md`.

Do not add speculation to memory files.

## Workflow requirement

Run each task according to `.codex/WORKFLOW.md`.
