# New Chat Initialization Prompt

Use this when opening a fresh agent chat in this repository.

## New Loop Setup

Copy this prompt:

**Set up this repository as a new Document Study Loop. Read `AGENTS.md` and `skills/document-study-loop-setup/SKILL.md` first. Create a Git-safe local study workflow for my documents. Keep raw PDFs, slide decks, archives, secrets, and local editor state out of Git. Use Markdown run files in `exam-revision/runs/active/`, preserve answers when grading, update the study ledger, and treat `examples/` as reference material only.**

## Continue Existing Loop

Copy this prompt:

**Continue this existing Document Study Loop. Read `AGENTS.md` and `skills/document-study-loop-continue/SKILL.md` first. Summarize the current active runs, completed runs, source maps, and study ledgers. If an answer sheet is ready, grade it in place; otherwise propose the next Markdown run. Do not treat `examples/` as live study state.**

## Local Source Policy

Raw documents belong in `exam-revision/source/` and stay local-only by default. Do not ask the user to paste source content, secrets, or private document text into chat if a local file workflow is available.
