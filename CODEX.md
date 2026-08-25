@AGENTS.md
<!-- Codex config — imports AGENTS.md -->

# Codex Quickstart

This repository shares one workflow with Claude Code, OpenCode, and Gemini. Do not copy command logic into this file.

1. Install [Bun](https://bun.sh). Optional: LaTeX or Typst for local PDFs; optional `pip install pypdf` for the ATS check.
2. Run the `setup` mode using the `job-search` skill (`.claude/commands/setup.md`).
3. Find jobs: `job-search` skill, mode `scrape`.
4. Apply: `job-search` skill, mode `apply`, with the job URL.

Profile data lives in `CLAUDE.md` and `.claude/skills/job-application-assistant/` — there is no separate `config/` directory.
