# AI Job Search: Architecture & Plan 

## Overview
This repository uses a **Universal AI Agent Architecture** (sometimes referred to as the career-ops style). It is designed to ensure that your automated job search workflows work perfectly and identically across any AI framework (OpenCode, Claude Code, Antigravity, Codex, Gemini, etc.) with absolutely **zero logic drift**.

## Core Architectural Pillars

### 1. The Single Source of Truth (`AGENTS.md`)
This architecture uses a thin-pointer design so runtimes do not each keep their own copy of the workflow.
- **`AGENTS.md`** is the index: rules, directory map, and pointers to canonical files.
- **`CLAUDE.md`** is the candidate profile that `/setup` writes. It is not a second copy of the workflow. OpenCode/Gemini/Codex load `OPENCODE.md` / `GEMINI.md` / `CODEX.md`, which import `@AGENTS.md`.
- Profile details also live in `.claude/skills/job-application-assistant/` (`01-candidate-profile.md`, etc.).

### 2. Universal Workflow Logic (`.claude/commands/`)
Workflow logic (how to evaluate a job, how to scrape, how to apply) is **not** hidden in tool-specific command folders.
- Core commands (`setup`, `scrape`, `apply`, `interview`, `rank`, …) are stored as markdown in `.claude/commands/`.
- Shared verification rules live in those command files and in `.claude/skills/job-application-assistant/` — there is no separate `_shared.md` in this tree.

### 3. Centralized Reference Data (`.claude/skills/job-application-assistant/`)
All candidate-specific data, methodologies, and templates live in `/.claude/skills/job-application-assistant/`. 
- When the user runs the `setup` mode, the AI parses their raw documents and generates highly structured files like `01-candidate-profile.md` and `04-job-evaluation.md`.
- These files are heavily referenced by the `.claude/commands/` scripts to generate tailored cover letters and CVs.

### 4. Intelligent Routers (`SKILL.md`)
To make the `.claude/commands/` accessible to native agent frameworks, we use Router Skills.
- Identical `SKILL.md` routers are placed in `.agents/skills/job-search/`, `.opencode/skills/job-search/`, and `.claude/skills/job-search/`.
- When a user asks an agent to "run setup" or "apply for this job", the agent uses the router skill to map the request directly to the corresponding script in `.claude/commands/`.

## Why This Architecture is 10/10
1. **Zero Drift:** All logic shares the `.claude/commands/` and `.claude/skills/job-application-assistant/` folders. Modifying a workflow once updates it for all AI tools.
2. **Backward Compatibility:** Claude Code slash commands in `.claude/commands/` remain the real workflows (`/setup`, `/scrape`, `/apply`, …). Other CLIs reach the same files through the `job-search` router.
3. **True Interoperability:** Whether you prefer OpenCode's rapid execution, Claude's deep reasoning, or Antigravity's autonomous workflows, the repository behaves identically.

## System Workflow Diagram
1. **User input** ➔ **AI Agent (OpenCode/Claude)**
2. **AI Agent** reads ➔ **Router Skill (`SKILL.md`)**
3. **Router Skill** triggers ➔ **Mode Script (`.claude/commands/apply.md`)**
4. **Mode Script** pulls data from ➔ **`AGENTS.md` & `.claude/skills/job-application-assistant/*.md`**
5. **AI Agent** executes logic ➔ **Outputs PDFs in `cv/` and `cover_letters/`**
