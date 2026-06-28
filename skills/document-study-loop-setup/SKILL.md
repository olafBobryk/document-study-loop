---
name: document-study-loop-setup
description: Set up, migrate, initialize, or clean a reusable file-based Document Study Loop project for document-, PDF-, slide-, transcript-, note-, or rubric-grounded study. Use when creating a new study loop, turning this template into a course/project instance, moving existing study state into the structure, checking public/private boundaries, or preparing Git/GitHub initialization.
---

# Document Study Loop Setup

## Overview

Use this skill to turn source documents and study state into a Git-safe Markdown study-loop repository. The repo should remain file-based: agents create answer sheets, the learner answers in Markdown, agents grade in place, and ledgers carry state across chats.

This skill supports four modes:

- **Blank setup:** initialize this template for a new document or course loop.
- **Migration setup:** import an existing study folder into the template structure.
- **Public-template cleanup:** keep only reusable docs, skills, templates, and tiny labeled examples.
- **Git/GitHub audit:** verify that raw/private source files and secrets will not be committed.

## Required First Pass

1. Inspect the project tree before editing.
2. Read `AGENTS.md`, `README.md`, and `.gitignore`.
3. Check whether `examples/` exists. Treat it as reference-only, never as live study state.
4. Identify live study state only from:
   - `study-ledgers/`
   - `exam-revision/notes/`
   - `exam-revision/runs/active/`
   - `exam-revision/runs/completed/`
   - `exam-revision/transcripts/`
   - `exam-revision/diagrams/`
5. Check source/privacy boundaries before Git.

## Setup Workflow

For a blank loop:

1. Ask the user to place local source documents in `exam-revision/source/` if needed.
2. Keep raw source documents ignored by Git.
3. Build or update `exam-revision/notes/topic_source_map.md`.
4. Build or update `exam-revision/notes/exam_question_patterns.md` when rubric or sample-question patterns exist.
5. Initialize `study-ledgers/study-loop-ledger.md` for the user's actual goals.
6. Create new practice runs only in `exam-revision/runs/active/`.

For a migrated loop:

1. Move active answer sheets to `exam-revision/runs/active/`.
2. Move graded/cancelled answer sheets to `exam-revision/runs/completed/`.
3. Move source maps, pattern maps, and rubric notes to `exam-revision/notes/`.
4. Move safe transcripts/summaries to `exam-revision/transcripts/`.
5. Leave raw PDFs, slide decks, archives, and private documents local-only in `exam-revision/source/`.
6. Fix old absolute paths or mark them local-only.

## File-Based Study Contract

- Create new practice runs as Markdown files in `exam-revision/runs/active/`.
- Do not ask full quizzes in chat when a run file exists.
- The learner answers directly under `Answer` headings.
- Grade in place without overwriting answers.
- Write grading notes into the same run file.
- Update the relevant ledger in `study-ledgers/`.
- Move graded/cancelled runs to `exam-revision/runs/completed/`.
- Generate altered variants by default. Use exact original prompts only when the user explicitly asks for a final-check, sample-exam, or calibration pass.

## Public and Git Safety

Before `git init`, commit, or push, audit for:

```sh
find . -type f \( -iname '*.pdf' -o -iname '*.ppt' -o -iname '*.pptx' -o -iname '*.key' -o -iname '*.zip' -o -name '.env*' \) -print
find . -type d \( -name '.vscode' -o -name '.idea' \) -print
```

Also search for absolute local paths and old source-folder names that are specific to the project being migrated.

Default policy:

- Do not commit raw course/source documents unless the user explicitly confirms they are safe to redistribute.
- Do not commit secrets or local-only setup files.
- Do not commit full transcripts of copyrighted/private material unless the user has redistribution rights.
- If pushing a reusable template to GitHub, keep examples tiny and clearly labeled.
- For ordinary personal study repos, prefer private GitHub unless the user explicitly requests public.

## Reference

For a detailed setup checklist, read `references/setup-checklist.md`.
