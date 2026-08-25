---
name: job-search
description: AI job search assistant — evaluate jobs, tailor CVs, write cover letters, prep interviews
arguments: mode
user_invocable: true
---

# job-search -- Router

This is a Universal Edition **router**, not a job-portal CLI. Portal scrapers live in sibling `*-search` folders that have a `cli/` directory. `/scrape` skips this folder.

## Mode Routing
| Input | Action |
|-------|--------|
| (empty) | Show command menu |
| `setup` | `.claude/commands/setup.md` |
| `apply <url>` | `.claude/commands/apply.md` |
| `interview` | `.claude/commands/interview.md` |
| `rank` | `.claude/commands/rank.md` |
| `scrape` | `.claude/commands/scrape.md` |
| `upskill` | `.claude/commands/upskill.md` |
| `outcome` | `.claude/commands/outcome.md` |
| `expand` | `.claude/commands/expand.md` |
| `html-report` | `.claude/commands/html-report.md` |
| `add-portal` | `.claude/commands/add-portal.md` |
| `add-template` | `.claude/commands/add-template.md` |
| `gmail-sync` | `.claude/commands/gmail-sync.md` |
| `notion-sync` | `.claude/commands/notion-sync.md` |
| `reset` | `.claude/commands/reset.md` |

## Context Loading
Read `AGENTS.md` for shared workflow rules, then `CLAUDE.md` and `.claude/skills/job-application-assistant/01-candidate-profile.md` for the candidate profile. Execute the requested mode file in `.claude/commands/`. Do not duplicate those files.
