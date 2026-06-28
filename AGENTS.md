# Agent Instructions

- Treat this as a file-based study-loop project, not a chat-only quiz.
- For setup, migration, Git/GitHub initialization, or repo audits, read `skills/document-study-loop-setup/SKILL.md` first.
- For a new chat in an already initialized loop, read `skills/document-study-loop-continue/SKILL.md` first.
- Never treat files under `examples/` as live study state.
- Do not put raw PDFs, sample exam PDFs, slide decks, zip archives, secrets, or local editor state into Git.
- Keep local source documents in `exam-revision/source/`; `.gitignore` keeps raw source files local-only.
- When creating new practice runs, use Markdown files in `exam-revision/runs/active/`.
- The user answers directly under `Answer` headings.
- When grading, preserve user answers, write grading notes into the same run file, update the relevant ledger in `study-ledgers/`, and move graded runs to `exam-revision/runs/completed/`.
- Generate altered variants rather than original sample questions unless the user explicitly requests a sample-exam, final-check, or exact calibration pass.
- Use `exam-revision/notes/topic_source_map.md`, `exam-revision/notes/exam_question_patterns.md`, and available local transcripts or notes to ground generated questions.
