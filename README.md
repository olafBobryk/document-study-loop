# Document Study Loop

![Document Study Loop banner](assets/document-study-loop-banner.png)

A lightweight template for file-based study with agents. It turns local PDFs, slides, notes, transcripts, and rubrics into durable Markdown answer sheets, graded runs, and study ledgers.

The repo is intentionally blank by default. Clone it, give an agent the setup prompt, add your own local source documents, and start a new loop.

## Instant Setup

Template repository: [https://github.com/olafBobryk/document-study-loop](https://github.com/olafBobryk/document-study-loop)

### First-Time Bootstrap

Copy this prompt into Codex or another coding agent when you have not cloned the template yet:

**Create a new Document Study Loop from `https://github.com/olafBobryk/document-study-loop`. Use environment variables when available: `STUDY_LOOP_DIR` for the local destination, `STUDY_LOOP_GITHUB_OWNER` and `STUDY_LOOP_GITHUB_REPO` for my own GitHub repository, and `STUDY_LOOP_VISIBILITY` for `private` or `public` visibility. Clone the template repo, rename its `origin` remote to `template`, create or connect my own Git remote if those GitHub variables are set, then read `AGENTS.md` and `skills/document-study-loop-setup/SKILL.md`. Set up a Git-safe local study workflow for my documents. Keep raw PDFs, slide decks, archives, secrets, and local editor state out of Git. Use Markdown run files in `exam-revision/runs/active/`, preserve answers when grading, update the study ledger, and treat `examples/` as reference material only.**

Equivalent shell-first setup:

```sh
export STUDY_LOOP_TEMPLATE_URL="https://github.com/olafBobryk/document-study-loop.git"
export STUDY_LOOP_DIR="${STUDY_LOOP_DIR:-$HOME/document-study-loop}"

git clone "$STUDY_LOOP_TEMPLATE_URL" "$STUDY_LOOP_DIR"
cd "$STUDY_LOOP_DIR"
git remote rename origin template

# Optional: create your own GitHub repo for this loop.
# Defaults to private for personal study material.
export STUDY_LOOP_VISIBILITY="${STUDY_LOOP_VISIBILITY:-private}"
if [ -n "$STUDY_LOOP_GITHUB_OWNER" ] && [ -n "$STUDY_LOOP_GITHUB_REPO" ]; then
  gh repo create "$STUDY_LOOP_GITHUB_OWNER/$STUDY_LOOP_GITHUB_REPO" \
    "--$STUDY_LOOP_VISIBILITY" \
    --source=. \
    --remote=origin \
    --push
fi
```

### Already Cloned

**Set up this repository as a new Document Study Loop. Read `AGENTS.md` and `skills/document-study-loop-setup/SKILL.md` first. Create a Git-safe local study workflow for my documents. Keep raw PDFs, slide decks, archives, secrets, and local editor state out of Git. Use Markdown run files in `exam-revision/runs/active/`, preserve answers when grading, update the study ledger, and treat `examples/` as reference material only.**

### Continue Existing Loop

**Continue this existing Document Study Loop. Read `AGENTS.md` and `skills/document-study-loop-continue/SKILL.md` first. Summarize the current active runs, completed runs, source maps, and study ledgers. If an answer sheet is ready, grade it in place; otherwise propose the next Markdown run. Do not treat `examples/` as live study state.**

## Included Skills

![Skills overview](assets/skills-overview.png)

This template carries two local skills for agents:

- `skills/document-study-loop-setup/SKILL.md` sets up a blank loop, migrates an existing study folder, audits Git safety, and prepares the repo for GitHub.
- `skills/document-study-loop-continue/SKILL.md` resumes work in an existing loop, checks current state, grades ready runs, or proposes the next run.

The setup skill creates the durable structure. The continue skill prevents new chats from starting over or accidentally using example files as live study state.

## Loop Breakdown

![Loop breakdown](assets/loop-breakdown.png)

The workflow stays file-based instead of turning into a long chat quiz:

1. Put source documents in `exam-revision/source/` locally. Raw source documents are ignored by Git.
2. Let an agent build or update `exam-revision/notes/topic_source_map.md` and `exam-revision/notes/exam_question_patterns.md`.
3. Let an agent create a Markdown run in `exam-revision/runs/active/`.
4. Answer directly under each `Answer` heading.
5. Ask the agent to grade the run in place, update `study-ledgers/study-loop-ledger.md`, and move the graded run to `exam-revision/runs/completed/`.

Generated practice should usually be altered variants grounded in your documents. Exact original sample questions should only be used when you explicitly request a final-check or calibration pass.

## Repository Layout

```text
.
├── AGENTS.md
├── NEW_CHAT_INIT_PROMPT.md
├── assets/
├── exam-revision/
│   ├── notes/
│   ├── runs/
│   │   ├── active/
│   │   ├── completed/
│   │   └── _templates/
│   ├── source/
│   ├── transcripts/
│   └── diagrams/
├── examples/
│   └── tue-2irr00-software-design/
├── skills/
│   ├── document-study-loop-setup/
│   └── document-study-loop-continue/
└── study-ledgers/
```

## Public Safety

This repo is designed to be public-template safe. Do not commit raw PDFs, slide decks, sample exams, archives, secrets, or local editor state. Keep those files local and let agents reference them through source maps, summaries, transcripts you are allowed to publish, or local-only paths.

The `examples/` folder shows the shape of a real loop without publishing source course files or full transcripts.

## Example

See `examples/tue-2irr00-software-design/` for a compact example based on a TU/e 2IRR00 Software Design study loop. It includes a tiny source map, a tiny ledger, and one answered-and-graded run. It is example-only and should not be used as live study state.
