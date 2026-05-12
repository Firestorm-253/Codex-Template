# Workflow

This file defines the standard Codex workflow for one task.

## Phase 1: Load context

1. Load the required context defined in `AGENTS.md`.
2. If `Task status` in `.codex/CURRENT_TASK.md` is `NOT SET`, stop without changing files.
3. Read only additional files explicitly referenced by the current task or required to understand touched code.

## Phase 2: Check scope

Before editing files, identify:

- the exact behavior requested,
- the smallest test that should fail first,
- the files likely to change,
- which memory files may need updates.

Stop and report if the task conflicts with an immutable contract file.

## Phase 3: Red

Execute the red phase defined in `.codex/TDD_CONTRACT.md`.

## Phase 4: Green

Execute the green phase defined in `.codex/TDD_CONTRACT.md`.

## Phase 5: Refactor

Refactor only as allowed by `.codex/TDD_CONTRACT.md`.

## Phase 6: Update memory

Update mutable memory files according to `.codex/memory/INDEX.md`.

Do not edit immutable contract files during this phase.

## Phase 7: Stop conditions

Stop and report instead of guessing if:

- the required behavior is ambiguous,
- required files do not exist and the task does not allow creating them,
- tests cannot be run because required tooling is missing,
- implementation would require changing immutable contract files,
- the task conflicts with `AGENTS.md`, `.codex/TDD_CONTRACT.md`, or `.codex/CURRENT_MILESTONE.md`.

## Phase 8: Completion gate

Before final response, verify:

- [ ] Only allowed files changed.
- [ ] Task-specific acceptance criteria in `.codex/CURRENT_TASK.md` are satisfied.
- [ ] TDD requirements in `.codex/TDD_CONTRACT.md` are satisfied, unless the task is documentation-only.
- [ ] Mutable memory files were updated or explicitly deemed unchanged.
- [ ] No immutable contract file was changed.
- [ ] No milestone-level or future work was implemented.

## Phase 9: Final response

Report:

- changed behavior,
- changed files,
- tests added or updated,
- commands run and results,
- memory files updated or explicitly unchanged,
- unresolved risks or questions.

Do not propose extra implementation work unless it is necessary to explain an unresolved risk.
