# Lesson 3 — Automation & Power Features

**After this lesson you'll be able to:** identify which power features are unique to each tool, so you know when a task calls for one specifically rather than "either one will do."

This is where the two tools diverge most. Claude Code's terminal-native design gives it automation/scripting depth; Cursor's editor-native design gives it in-editor workflow depth.

## Claude Code: slash commands

- Reusable, named prompts you invoke with `/command-name`, optionally with arguments — a way to save a multi-step instruction (e.g., a review checklist, a release routine) and re-run it instead of retyping it. Can be project-scoped (checked into the repo) or user-scoped.
- **Cursor counterpart:** no directly equivalent "slash command" system for arbitrary saved prompts in the same sense; check current docs, as Cursor's feature set is evolving quickly. If you rely on reusable saved workflows, this is presently a Claude Code strength.

## Claude Code: hooks

- Shell commands that fire automatically at defined points in the agent's lifecycle (e.g., before/after a tool call, on session start/stop) — used for things like auto-formatting after an edit, blocking a dangerous command, or logging activity.
- **Cursor counterpart:** none directly equivalent for hooking into the AI agent's lifecycle itself. Editor-level automation in Cursor generally means falling back to normal VS Code extension/task mechanisms rather than an AI-agent-specific hook system.

## Claude Code: headless / scripting mode

- Claude Code can run non-interactively — invoked from a script or CI pipeline, given a prompt, and left to run to completion and exit, producing output you can capture. This is what makes it usable as an automation building block, not just a chat interface.
- **Cursor counterpart:** Cursor is fundamentally an interactive editor experience; it's not designed to be driven headlessly from CI in the same way. This is a core Claude Code strength for anything you want to run unattended.

## Claude Code: permission modes

- Control how much Claude Code can do without asking — ranging from confirming every file edit/command to running more autonomously. Lets you dial autonomy up or down per task or per session.
- **Cursor counterpart:** Cursor's agent/Composer mode has its own settings around auto-run/auto-accept of edits and commands; check current docs for exact terminology and current granularity. Conceptually similar (a dial on autonomy), implemented separately.

## Cursor: custom modes

- Configure named modes with their own tool access, instructions, or behavior bias (e.g., a "planning-only, no edits" mode) that you switch between depending on task. The closest Cursor analog to Claude Code's plan mode from Lesson 1.
- **Claude Code counterpart:** plan mode and permission modes cover similar ground (constraining what the agent is allowed to do), but Claude Code doesn't have a general "define your own named modes" system in the same way — check current docs.

## Cursor: background agents

- Cursor can run an agent on a task in the background (e.g., in a remote/cloud environment) while you keep working, rather than blocking your editor session on a long agentic task. Check current docs for exact setup and current capabilities/limits.
- **Claude Code counterpart:** you can approximate this by running Claude Code in a separate terminal/tab, or via its headless/scripting mode kicked off asynchronously, but it's not a built-in "background agent" product feature — it's a consequence of Claude Code being a plain terminal process you can back and detach at will.

## Cursor: terminal integration

- Cursor, being VS Code-based, has a full integrated terminal, and its agent can be given the ability to run terminal commands as part of its edits.
- **Claude Code counterpart:** Claude Code *is* effectively a terminal-native tool already — running commands is core to how it operates, not an add-on. If your task is terminal-heavy, this is Claude Code's home turf.

## Try it

Think of one repetitive task you do often in this repo (running a specific check, a formatting pass, a routine multi-step review). In Claude Code, save it as a slash command (or sketch what the command would look like) and consider whether a hook could automate a step of it. Then check Cursor's current docs for whether/how a similar saved-workflow concept exists there today. The gap you find is real signal for which tool to lean on for automation-heavy work.
