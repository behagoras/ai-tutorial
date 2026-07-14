# Lesson 0 — Setup & Mental Model

**After this lesson you'll be able to:** install and authenticate both tools, and know which one to open for a given kind of work based on their core architectural difference.

## The core distinction

- **Claude Code** is a terminal-native agentic CLI. It runs as a process in your shell, reads/writes files, runs commands, and drives git — all from a conversational loop, in whatever editor or terminal you already use. It is editor-agnostic; there are also IDE extensions (VS Code, JetBrains) that embed it, but the primary surface is the terminal.
- **Cursor** is an AI-native code editor — a fork of VS Code. AI is woven into the editing surface itself: inline completions as you type, inline edit commands, and an agent mode, all inside the editor UI. It replaces your editor rather than living alongside it.

Rough analogy: Claude Code is a very capable pair-programmer you talk to in the terminal who happens to also be able to edit files and run commands. Cursor is VS Code with that pair-programmer built into the fabric of the editor — cursor position, keystrokes, and all.

This difference shapes everything downstream: Claude Code composes well with any editor, scripts, CI, and headless automation. Cursor's strength is a tight, low-latency loop between your cursor position and AI suggestions inside one editor.

## Install & authenticate

- **Claude Code**: install per the official docs (npm package `@anthropic-ai/claude-code`, or check current docs for the latest install method). Authenticate with an Anthropic account or API key when prompted on first run.
- **Cursor**: download the app from the official site, install like any editor, sign in with a Cursor/GitHub account on first launch.

Check current docs for both — install methods and pricing tiers change.

## One-glance feature map

| Capability | Claude Code | Cursor |
|---|---|---|
| Where it lives | Terminal (+ IDE extensions) | Standalone editor (VS Code fork) |
| Inline "as you type" completion | No (not its model) | Yes — Tab |
| Inline selection edit | Via chat/agent in terminal or extension | Yes — inline edit (Cmd/Ctrl+K family; check current docs for exact shortcut) |
| Multi-file agentic edits | Yes — core mode | Yes — Composer/Agent mode |
| Plan-before-edit mode | Yes — plan mode | Custom modes can approximate this |
| Project memory file | CLAUDE.md | .cursor/rules |
| Scripting / headless / CI use | Yes — first-class | Not its primary design; check current docs |
| Runs outside an editor | Yes | No |

Each of these gets a full lesson; this table is just the map.

## Try it

Open a repo you know well. Launch Claude Code in its terminal in that directory, and separately open the same repo in Cursor. In each, ask (in your own words) "what does this codebase do, at a high level?" Notice where the answer comes from — Claude Code reading files via tool calls in a running conversation, versus Cursor's chat panel inside the editor. That felt difference is the mental model to carry into the next lessons.
