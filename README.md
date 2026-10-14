# plan-t_helper

A tool-independent AI helper system for the Plan-t project. It gives any advanced LLM (coding agents such as Codex or Claude Code, and chat assistants such as ChatGPT, Claude or Gemini) the same rules, the same project facts and the same shared log, so work stays in scope and in context across sessions and tools.

Version: see VERSION. Provider: Anıl Ediz. Project owner: Tuğberk.

## What is in this repository

| Folder | Goes where in the Plan-t repo | Who changes it |
|---|---|---|
| core/ (CORE.md, PLANNER.md, CORE-CHANGELOG.md) | agentic/ | Provider only, through new releases |
| adapters/ (AGENTS.md, CLAUDE.md) | repository root | Provider only |
| project-template/ (PROJECT.md, log/) | agentic/ (first install only) | Project owner |

## Install (first time)

1. In the Plan-t repository root, create a folder named agentic.
2. Copy everything from core/ into agentic/.
3. Copy everything from project-template/ into agentic/ (PROJECT.md and the log folder).
4. Copy AGENTS.md and CLAUDE.md from adapters/ into the repository root. If a file with the same name already exists there, do not overwrite it: keep the existing text and add the adapter's lines at the top.
5. Open agentic/PROJECT.md and check every line marked UNVERIFIED against your repository.
6. Paste the text of agentic/PLANNER.md into your chat assistant's project or custom instructions.
7. Commit.

## Update (new version)

1. Replace the files in agentic/ that came from core/ (CORE.md, PLANNER.md, CORE-CHANGELOG.md).
2. Replace AGENTS.md and CLAUDE.md lines that came from adapters/.
3. Never overwrite agentic/PROJECT.md or agentic/log/. They are your project's own facts and history.
4. Re-paste PLANNER.md into your chat assistant.
5. Read the newest entry in CORE-CHANGELOG.md to see what changed.

## How a work session runs

1. Plan with the chat assistant. It summarises where the project stands, splits the goal into 1–6 sessions and writes one brief per session.
2. Give one brief to the coding agent. It restates the session, works only inside it, runs targeted tests and writes a report into agentic/log/sessions/ plus one row in agentic/log/PROJECT-LOG.md.
3. Check the UI yourself in the browser.
4. Paste the report back to the chat assistant. It answers ACCEPT, REVISE or BLOCKED.

If an agent says "This is a critical CORE change", contact the provider. Everything specific to your project lives in agentic/PROJECT.md, which you can change yourself.
