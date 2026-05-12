# TDD Contract

This file defines the required test-driven-development rules for code behavior changes.

## Core rule

Write or update a failing test before implementing behavior.

The required sequence is:

1. Identify the smallest behavior required by `.codex/CURRENT_TASK.md`.
2. Add or update the smallest meaningful test for that behavior.
3. Run the smallest relevant test command.
4. Confirm the test fails for the expected reason.
5. Implement the minimum code needed to pass.
6. Run the relevant tests again.
7. Refactor only after the relevant tests pass.
8. Run the relevant tests again after refactoring.

## Valid failing test

A valid failing test must:

- describe behavior required by `.codex/CURRENT_TASK.md`,
- fail before implementation,
- fail for the expected reason,
- avoid failure caused by syntax errors, broken imports, or unrelated failures,
- be specific enough to catch a regression.

## Minimum implementation

After the failing test exists, implement only what is needed to pass the test and satisfy `.codex/CURRENT_TASK.md`.

Do not add unrelated abstractions, features, integrations, or future-proofing unless the current task explicitly requires them.

## Refactoring

Refactoring is allowed only after the relevant tests pass.

Refactoring must preserve behavior and must not expand the task scope.

## Documentation-only tasks

A task may skip the red/green loop only when it changes no executable behavior.

For documentation-only tasks, Codex must report:

- why no test was added,
- which files changed,
- whether any executable behavior changed.

## Test command

Use the smallest useful test command first.

Examples:

- a single test file when the task touches one behavior,
- a package-level test when several files interact,
- the full suite only when needed for confidence or when the task requires it.

If the project has no test command yet, the current task must either define one or explicitly allow creating the test harness.

## Broken baseline

If existing tests fail before any changes:

1. Record the baseline failure.
2. Do not fix unrelated failures unless the current task requires it.
3. Continue only if the current task can be isolated.
4. Report the baseline failure.
