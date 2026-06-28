# Setup Checklist

Use this checklist when initializing, migrating, auditing, or publishing a Document Study Loop project.

## Required Structure

```text
.
├── README.md
├── AGENTS.md
├── NEW_CHAT_INIT_PROMPT.md
├── .gitignore
├── assets/
├── study-ledgers/
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
└── skills/
    ├── document-study-loop-setup/
    └── document-study-loop-continue/
```

## Privacy Audit

Run before Git initialization, commit, or push:

```sh
find . -type f \( -iname '*.pdf' -o -iname '*.ppt' -o -iname '*.pptx' -o -iname '*.key' -o -iname '*.zip' -o -name '.env*' \) -print
find . -type d \( -name '.vscode' -o -name '.idea' \) -print
```

Expected public-template result: no raw source documents, archives, secrets, or editor folders.

## Link Audit

Search for migration-sensitive links, including absolute local paths and old source-folder names that are specific to the project being migrated.

For each result:

- Remove absolute local paths from reusable docs.
- Keep source paths only when they describe local-only behavior.
- Keep course references only under clearly labeled example docs.

## Run-State Audit

Check active/completed state:

```sh
find exam-revision/runs/active -maxdepth 1 -type f -print | sort
find exam-revision/runs/completed -maxdepth 1 -type f -print | sort
```

For a blank template, only `.gitkeep` placeholders should appear.

## Git Initialization

Only after audits pass:

```sh
git init
git add .
git commit -m "Initialize document study loop template"
```

Default GitHub behavior:

- Public is acceptable for the reusable template when it contains no raw/private source content.
- Private is safer for personal study repos unless the user explicitly requests public.
