# Memory Index

This directory contains mutable working-memory files for Codex.

The goal is to preserve useful project facts without relying on chat history.

## Files

- `project_state.md` — current implementation status, known issues, last completed task, and test status.
- `architecture.md` — current implemented architecture, module boundaries, and important technical shape.
- `open_questions.md` — unresolved questions that should not be guessed or silently resolved.
- `glossary.md` — domain terms, project vocabulary, and naming conventions.

## Update rules

Codex may update lowercase memory files when the current task changes their facts.

Memory files must be:

- factual,
- current,
- concise,
- tied to actual implementation or explicit decisions.

Memory files must not contain:

- speculative roadmap ideas,
- unrelated brainstorming,
- abandoned alternatives.

## Conflict rule

If a memory file conflicts with an immutable contract file, stop and report the conflict.

Record the conflict in `open_questions.md` only if it is relevant after the task stops.
