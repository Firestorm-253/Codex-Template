# Glossary

This file is mutable working memory.

It defines project vocabulary and domain terms so Codex uses names consistently.

## Update guidance

Add terms when the project introduces domain vocabulary, naming conventions, or concepts needed for future tasks.

Keep definitions short and concrete.

## Terms

### Contract file

An owner-authored Markdown file with an ALL_CAPS name.

### Memory file

A lowercase Markdown file that Codex may update when the current task changes the facts it describes.

### Current task

The task packet stored in `.codex/CURRENT_TASK.md`.

### Current milestone

The milestone context stored in `.codex/CURRENT_MILESTONE.md`.

### TDD

Test-driven development.

Active rules are defined in `.codex/TDD_CONTRACT.md`.

### Red phase

The TDD phase where a test is added or updated and confirmed to fail for the expected reason.

### Green phase

The TDD phase where the minimum implementation is added so the relevant test passes.

### Refactor phase

The TDD phase after green tests where code can be cleaned up without changing behavior.
