# Lesson 2 — Context & Steering

**After this lesson you'll be able to:** give each tool durable project context and narrow its attention to the right files, using the mechanism native to whichever tool you're in.

Both tools face the same problem — an LLM doesn't inherently know your codebase's conventions, architecture, or which files matter for a given task. Each has its own answer.

## Persistent project memory

- **Claude Code: `CLAUDE.md`** — a markdown file (project root, and optionally nested in subdirectories) that Claude Code reads automatically for standing instructions: conventions, architecture notes, "always do X," "never do Y." There's also a user-level global CLAUDE.md for cross-project preferences.
- **Cursor: `.cursor/rules`** — project rule files that similarly give Cursor standing context/instructions, scoped to the project (and rules can target specific paths/glob patterns). Check current docs for the exact file format, since it has evolved (from a single `.cursorrules` file to a `.cursor/rules/` directory of rule files).
- Side by side: functionally the same idea — a checked-in file (or files) telling the AI how to behave in this codebase — expressed differently. Both are worth setting up early; they compound over every session.

## Pointing at specific context

- **Claude Code: `@`-file references** — in the conversation, reference a file or path with `@` to pull it into context explicitly, rather than relying on the agent to discover it by searching.
- **Cursor: `@`-symbols** — `@files`, `@docs`, `@web`, and similar tokens in the chat/composer input to scope context: a specific file, a documentation source, or a live web reference. Broader in kind (docs, web) than Claude Code's file-focused `@`.
- Side by side: both use `@` as the "pull this specific thing into context" convention — muscle memory transfers, but the range of things you can point at differs. Check current docs for the current full list of `@` targets in each.

## Codebase-wide awareness

- **Cursor: codebase indexing** — Cursor indexes your project so it can retrieve relevant files/snippets automatically without you naming them, powering chat and agent answers about "unfamiliar" parts of the repo.
- **Claude Code:** doesn't pre-build a persistent semantic index in the same way; it explores the codebase live each session using its file/search tools (reading, grepping, listing directories) as part of the agent loop. Practically, both end up finding the relevant code — Cursor leans on a pre-built index, Claude Code leans on live tool-driven exploration.

## Extending capability: subagents & MCP (Claude Code)

- **Subagents** — Claude Code can delegate a sub-task to a separate agent instance with its own context window and tool access, useful for parallelizable or isolated research/work without polluting your main conversation.
- **MCP (Model Context Protocol)** — Claude Code can connect to MCP servers to pull in external tools/data sources (e.g., issue trackers, internal docs, databases) as first-class tools it can call.
- **Cursor counterpart:** Cursor also supports MCP server connections (check current docs for setup and current capabilities). Cursor does not have a directly named "subagents" concept in the same sense; if you need multiple isolated agent contexts working in parallel, that's a Claude Code strength — see Lesson 3 on background agents for Cursor's closer analog.

## Try it

In a repo you're not deeply familiar with (or pretend you're not), ask each tool the same question — "where is X handled, and what would I need to change to add Y?" — without pointing it at any specific file. Compare how each one found its way to the relevant code: Cursor's index-backed retrieval vs. Claude Code's live exploration. Then try scoping the same question with an explicit `@`-reference in each and see how much faster/more precise the answer gets.
