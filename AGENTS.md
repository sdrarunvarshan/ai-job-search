---
framework_version: 1.0.0
---

# Agent Guidelines: AI Job Search

This workspace is structured to manage job search activities, scraper tools, CVs, cover letters, and interview preparation.

## Thin-Pointer Design (Single Source of Truth)

To prevent duplication and configuration drift across different AI agent frameworks (Claude Code, OpenCode, Google Antigravity, Codex, Cursor, Gemini CLI, etc.), this workspace uses a unified thin-pointer design. Runtime-specific files (`OPENCODE.md`, `GEMINI.md`, `CODEX.md`) only point here. `CLAUDE.md` remains the **candidate profile** that `/setup` writes — do not replace it with another copy of these rules.

All agent runtimes should load the canonical specifications and candidate profiles from the files and directories below:

1. **Personal Candidate Profile:**
   - The candidate profile, contact details, education, and target preferences are defined in [CLAUDE.md](CLAUDE.md) and the individual profile methodology files under [.claude/skills/job-application-assistant/](.claude/skills/job-application-assistant/) (specifically `01-*.md` etc.).
2. **Canonical Workflow Specifications (modes):**
   - The step-by-step instructions and triggers for tasks (setup, scrape, rank, apply, upskill, interview) are defined in [.claude/commands/](.claude/commands/) and [.claude/skills/](.claude/skills/).
   - OpenCode / Gemini / Codex / Claude Code all execute those same files. The `job-search` router skill (`.agents/skills/job-search/`, `.claude/skills/job-search/`, `.opencode/skills/job-search/`) maps "run setup" / "run apply" to the matching command file.
   - Do not duplicate these rules or specifications. Treat `.claude/` files as the single source of truth.
3. **Portal Search Skills:**
   - Job-portal search CLIs live under [.agents/skills/](.agents/skills/) in the portable Agent Skills format (with a `SKILL.md` per portal **and** a `cli/` directory). Codex and Antigravity discover these automatically; the `/scrape` workflow in [.claude/skills/job-scraper/](.claude/skills/job-scraper/) orchestrates them.
   - This fork ships Denmark demos, LinkedIn/Freehire, **India market** portals (Apna, Hirist, IIMJobs, Instahyre, Indeed India, Randstad India, Cutshort, AIJobs, Foundit, ProtocolJobs), and **remote boards** (Himalayas, RemoteOK, WeWorkRemotely, Y Combinator, Otta).
   - Skip `job-search` when scraping — that folder is the Universal Edition router, not a portal CLI.

Architecture notes: [ai-job-search-plan.md](ai-job-search-plan.md).
