---
name: future-roadmap-planner
description: Brainstorm future product or engineering roadmap ideas from scratch, then turn the selected direction into milestones and tasks that follow `.codex/CURRENT_MILESTONE` and `.codex/CURRENT_TASK` templates exactly. Use when the user asks for roadmap planning, milestone generation, task breakdowns, future feature planning, initiative planning, or converting speculative ideas into Codex-ready work items.
---

# Future Roadmap Planner

Use this skill to help the user explore a not-yet-existing roadmap and convert it into structured milestone and task files.

The workflow is planning-first. Do not implement code unless the user explicitly asks for implementation after the roadmap, milestones, and tasks have been accepted.

## Required template files

Before generating any milestone or task content, inspect these files:

- `.codex/CURRENT_MILESTONE`
- `.codex/CURRENT_TASK`

Treat them as formatting contracts.

Use their structure, headings, metadata fields, checkbox style, status fields, naming conventions, and ordering exactly. Preserve any conventions implied by comments, placeholders, section labels, examples, or front matter.

If one or both files are missing, unreadable, empty, or ambiguous:

1. State what is missing.
2. Ask the user to provide the template files or approve a temporary fallback format.
3. If the user asked to proceed without clarification, create clearly marked drafts using a minimal fallback format and explain that they must be re-rendered once the templates are available.

## Activation goals

When this skill is active, help the user do one or more of the following:

- Brainstorm a future roadmap that does not exist yet.
- Convert vague product or engineering direction into candidate initiatives.
- Organize initiatives into coherent milestones.
- Decompose milestones into actionable tasks.
- Write milestone files using `.codex/CURRENT_MILESTONE` as the template.
- Write task files using `.codex/CURRENT_TASK` as the template.
- Identify dependencies, risks, assumptions, open questions, and validation criteria.
- Produce files that can be committed to the repository or used as planning artifacts.

## Operating principles

- Start broad, then converge.
- Prefer user intent over implementation convenience.
- Separate brainstorming from commitment.
- Avoid pretending uncertain plans are finalized.
- Make assumptions explicit.
- Keep scope realistic.
- Every milestone must describe a user-visible or project-visible outcome.
- Every task must be independently understandable and verifiable.
- Do not create vague tasks such as “improve system” or “research feature” unless the task includes concrete outputs and acceptance criteria.
- Do not overwrite existing roadmap, milestone, or task files unless the user explicitly asks.
- Do not modify `.codex/CURRENT_MILESTONE` or `.codex/CURRENT_TASK`; they are templates.
- Do not invent dates, owners, dependencies, or constraints as facts. Use `TBD` or an explicit assumption where needed.

## Roadmap brainstorming workflow

### 1. Gather context

First inspect repository context if available:

- README files
- `AGENTS.md`
- existing `.codex` planning files
- docs, product notes, architecture notes, or issue trackers present in the repo

Then summarize the relevant planning context briefly.

If context is insufficient, ask up to 5 focused questions. Prefer questions about:

- Target user or stakeholder
- Desired future outcome
- Business or technical constraints
- Time horizon
- Quality bar
- Current product maturity
- Known non-goals

If the user asks for immediate generation or wants to brainstorm freely, proceed using clearly labeled assumptions instead of blocking.

### 2. Generate candidate roadmap directions

Produce 3 to 7 candidate roadmap directions. For each direction include:

- Name
- Problem or opportunity
- Expected outcome
- Why now
- Risks
- Required discovery
- Rough complexity
- Confidence level

Keep candidate directions distinct. Avoid multiple variations of the same idea unless they represent genuinely different strategies.

### 3. Converge on a roadmap shape

Help the user select or combine directions. If the user does not choose, recommend one default roadmap shape and explain the tradeoff.

Convert the selected direction into a milestone sequence.

A good milestone sequence should:

- Show clear progression.
- Avoid hidden prerequisites.
- Deliver value before perfection.
- Include validation before large build-out.
- Separate foundation work from user-facing work when needed.
- Avoid milestones that are merely buckets of unrelated tasks.

### 4. Define milestones

For each milestone, determine:

- Milestone title
- Goal
- Scope
- Non-goals
- Deliverables
- Acceptance criteria
- Dependencies
- Risks
- Open questions
- Suggested tasks
- Validation or test approach
- Rollout or completion signal

Map these fields into the exact structure required by `.codex/CURRENT_MILESTONE`.

If the template lacks an obvious location for a field, either:

- Fit the information into the closest matching template section, or
- Omit it from the file and mention it separately as planning context.

Do not add new sections unless the user permits changing the template convention.

### 5. Decompose tasks

For each milestone, create tasks that are small enough to execute independently.

A good task should include:

- A single primary outcome
- Clear context
- Concrete implementation or planning steps
- Acceptance criteria
- Validation steps
- Dependencies
- Files or components likely involved, if known
- Out-of-scope notes
- Completion signal

Map each task into the exact structure required by `.codex/CURRENT_TASK`.

Avoid tasks that are too large. Split a task if it mixes discovery, implementation, testing, rollout, or documentation in a way that would make completion ambiguous.

## File generation behavior

When asked to create files:

1. Read `.codex/CURRENT_MILESTONE` and `.codex/CURRENT_TASK`.
2. Infer existing repository planning conventions.
3. Propose file paths before writing, unless the user explicitly requested direct edits.
4. Prefer stable, sortable paths such as:
   - `.codex/milestones/<NN>-<milestone-slug>.md`
   - `.codex/tasks/<milestone-slug>/<NN>-<task-slug>.md`
5. If the repository already has a different convention, follow the existing convention.
6. Generate milestone files first, then task files.
7. Keep generated content aligned with the templates.
8. After writing files, provide a concise summary of:
   - Created files
   - Milestones covered
   - Number of tasks created
   - Key assumptions
   - Open decisions

Do not overwrite existing files unless the user explicitly asks. If a target path already exists, propose a new path or ask before replacing it.

## Template fidelity rules

When using `.codex/CURRENT_MILESTONE` or `.codex/CURRENT_TASK`:

- Preserve section order.
- Preserve field names.
- Preserve front matter keys.
- Preserve checkbox syntax.
- Preserve heading levels.
- Preserve placeholder semantics.
- Preserve status vocabulary if present.
- Preserve date format if present.
- Preserve ID format if present.
- Preserve task-to-milestone reference style if present.
- Replace placeholders with content only where the template expects content.
- Leave unknown required values as `TBD` unless the template uses a different placeholder convention.

Before finalizing generated files, check that every required template field is filled or explicitly marked as unknown.

## Suggested interaction pattern

When brainstorming, use this structure:

1. “Here are the assumptions I’m using.”
2. “Here are candidate roadmap directions.”
3. “Here is the recommended milestone sequence.”
4. “Here is the proposed task breakdown.”
5. “Here are the files I would create or update.”

When the user asks for direct generation, skip extended discussion and produce the files, but still include assumptions and open questions in the result.

## Quality checklist

Before responding, verify:

- The two template files were inspected or their absence was handled.
- Milestones follow `.codex/CURRENT_MILESTONE`.
- Tasks follow `.codex/CURRENT_TASK`.
- The roadmap is internally coherent.
- Each milestone has a clear outcome.
- Each task has a verifiable completion condition.
- Dependencies are explicit.
- Risks are not hidden.
- Unknown facts are marked as assumptions or `TBD`.
- No implementation work was done unless requested.
- Existing files were not overwritten without permission.

## Example prompt this skill should handle

> Brainstorm a future roadmap for this project from scratch. Use `.codex/CURRENT_MILESTONE` and `.codex/CURRENT_TASK` as templates, then generate the first three milestones and their tasks.

Expected behavior:

1. Inspect the templates.
2. Inspect relevant repository context.
3. Propose a roadmap direction if none is given.
4. Generate milestone drafts using the milestone template.
5. Generate task drafts using the task template.
6. Propose or create file paths according to repository convention.
7. Summarize assumptions, created artifacts, and remaining decisions.
