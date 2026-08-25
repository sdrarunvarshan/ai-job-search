@AGENTS.md
<!-- OpenCode config — imports AGENTS.md -->

> **OPENCODE SYSTEM INSTRUCTION:**
> You are operating in the `ai-job-search` workspace. **Do not invent workflows.**
> Your single source of truth is `AGENTS.md` plus `.claude/commands/`.
> When the user triggers a mode (setup, scrape, apply, etc.), read and execute those files.

# OpenCode Quickstart

1. Install [Bun](https://bun.sh). Optional: LaTeX (`lualatex` / `xelatex`) or [Typst](https://typst.app/) if you want local PDFs; optional `pip install pypdf` for the ATS text-layer check.
2. In this directory, run the `setup` command from `.claude/commands/` (or: `job-search` skill, mode `setup`).
3. Find jobs: run `scrape` from `.claude/commands/`.
4. Apply: run `apply` from `.claude/commands/` with a job URL or pasted posting.

Profile data is written to `CLAUDE.md` and `.claude/skills/job-application-assistant/`. Do not duplicate it here.
