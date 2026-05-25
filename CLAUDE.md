# next_silence_note — Knowledge Base for Learning Next.js

This is a **personal learning repository** for Next.js 16. Same system as
`postgres_silence_note` — structured notes, exercises, and practical sub-projects
combined into a single knowledge base, streamed live on YouTube.

## Why This Exists

Learning Next.js from scratch in public: each session is recorded as a YouTube
stream, documented in `sessions/`, and reinforced with a coding exercise in
`examples/`. The goal is to build real understanding, not just follow tutorials.

## Repository Layout

```
next_silence_note/
├── sessions/       ← per-session notes (date-named, e.g. 2026-05-22.md)
├── exercises/      ← coding exercises with hints and solutions
├── examples/       ← practical sub-projects (one per session/topic)
│   └── nextjs_01/  ← sub-project #1: project setup & App Router basics
├── cheatsheets/    ← quick-reference cards (e.g. app-router-files.md)
├── templates/      ← templates for sessions, exercises, notes, etc.
├── youtube/        ← stream prep notes and scripts
├── ROADMAP.md      ← 10-phase learning plan (setup → deployment)
├── PROGRESS.md     ← session log and status
├── RESOURCES.md    ← curated docs, courses, tools
└── glossary.md     ← Next.js / React terminology
```

## Sub-Projects (examples/)

Each session has a corresponding coding project in `examples/`. These are
**real Next.js apps**, not stubs — run them with `yarn dev` to see the result.

| Dir          | Session | Topic                                       |
|--------------|---------|---------------------------------------------|
| `nextjs_01/` | #2      | Project setup, ESLint/Prettier, absolute imports |

Each sub-project has its own `CLAUDE.md` with stack details, structure, and
what has been covered so far.

## Current Progress

- **Phase 1** — Getting Started (in progress)
- Sessions 1–2 completed: repo scaffolding, project setup, App Router basics,
  ESLint + Prettier, absolute imports (`baseUrl: "src/"`)
- Next: Exercise 01 (`exercises/ex-01-first-routes.md`) — 3-page App Router site

## Working Conventions

- Package manager: **yarn** (not npm)
- Language: TypeScript throughout
- Session notes are written in Ukrainian
- Each session ends with a coding exercise in `examples/`
- Exercises use `<a href>` until `Link` is taught; then they get updated
