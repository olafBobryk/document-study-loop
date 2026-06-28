---
name: document-study-loop-continue
description: Continue work in an existing file-based Document Study Loop repository. Use in a new chat when the loop has already been set up and the agent needs to summarize status, grade a ready Markdown run, create the next run, or resume from ledgers without treating examples as live state.
---

# Document Study Loop Continue

## Overview

Use this skill when the repository is already a Document Study Loop and the user wants to continue studying, grade a run, or see current status. The goal is continuity: read the files, infer the live state, and keep the loop moving without restarting setup.

## Required First Pass

1. Read `README.md` and `AGENTS.md`.
2. Inspect these live-state locations:
   - `study-ledgers/`
   - `exam-revision/notes/`
   - `exam-revision/runs/active/`
   - `exam-revision/runs/completed/`
   - `exam-revision/transcripts/`
   - `exam-revision/diagrams/`
3. Do not treat anything under `examples/` as live state.
4. Report active runs, recent completed runs, current ledger status, and the next likely action.

## Continue Workflow

If an active run exists:

1. Read the run file.
2. Determine whether answers have been filled under `Answer` headings.
3. If answers are present and the user asked for grading, grade in place.
4. Preserve all user answers.
5. Write grading notes and scores into the same run file.
6. Update the relevant ledger in `study-ledgers/`.
7. Move the graded run to `exam-revision/runs/completed/`.

If no active run exists:

1. Read the ledger and source maps.
2. Identify open, repair, or test-stage topics.
3. Propose or create the next run according to the repo's current ledger rules.
4. Create the run in `exam-revision/runs/active/`.

If state is ambiguous:

1. Prefer file evidence over chat memory.
2. Ask only for decisions that cannot be resolved from the repo.
3. Do not invent source files, scores, or completed work.

## Grading Contract

- Preserve user answers exactly.
- Grade against the repo's rubric or pattern map.
- Mark uncertainty explicitly when the source material is missing.
- Update ledger status and next actions.
- Move graded/cancelled runs out of `active/`.

## Output Expectations

End with:

- active run status
- ledger changes made
- completed run path, if any
- next recommended action
