# Lesson 1 — Editing & Generation

**After this lesson you'll be able to:** pick the right editing mode — autocomplete, single-spot inline edit, or multi-file agentic change — in whichever tool you're in, and know its counterpart in the other.

## Cursor: Tab completion

- As you type, Cursor predicts the next edit (not just the next token) — completions can span multiple lines and jump to nearby locations in the file.
- Best for: mechanical, in-flow edits where you're already mid-thought — finishing a function body, propagating a rename-like change nearby.
- **Claude Code counterpart:** none. Claude Code has no keystroke-level autocomplete; it's not part of its model. If you're in a Claude Code-only workflow, this class of "flow-state completion" simply isn't there — that's a real reason to keep an editor with Tab-style completion in your loop.

## Cursor: Inline edit (Cmd/Ctrl+K family)

- Select code (or a location), invoke inline edit, describe the change in natural language, get a diff applied right there. Check current docs for the exact current shortcut — it has shifted across versions.
- Best for: a scoped, single-location edit where you already know exactly what to change and just don't want to type it by hand.
- **Claude Code counterpart:** asking Claude Code directly to "edit this function to do X" in the terminal conversation, referencing the file. Same intent, different surface — Claude Code doesn't have a shortcut bound to your cursor's current selection, you tell it what/where in words (or with an @-file reference, covered in Lesson 2).

## Claude Code: agentic multi-file edits

- Claude Code's default mode: you describe a task, it reads relevant files, plans, edits across as many files as needed, runs commands (tests, builds, linters) to check its own work, and iterates — all in one conversational loop.
- Best for: changes that cross file boundaries — a refactor that touches a function and all its call sites, adding a feature that needs a new file plus wiring elsewhere.
- **Cursor counterpart:** Composer / Agent mode — Cursor's own multi-file agentic mode, invoked from the chat/composer panel rather than the terminal. Conceptually the same capability; the difference is surface (editor UI vs. terminal) and how deeply each integrates with running commands/tests as part of its loop — check current docs for the current depth of Cursor's agent tool-use.

## Claude Code: plan mode

- Ask Claude Code to plan before it touches anything — it reads the codebase, proposes an approach and a set of steps, and waits for your go-ahead before editing. Useful for anything you don't want to just let rip on the first pass.
- **Cursor counterpart:** there's no identically-named "plan mode," but Cursor's custom modes (Lesson 3) can be configured to bias toward read-only/planning behavior before editing. Check current docs for the closest current equivalent — don't assume feature parity here.

## Try it

Pick a small, real change in your own repo that touches at least two files (e.g., a function signature change and its call sites). Do it once in Claude Code as a single agentic instruction. Do it once in Cursor using Composer/Agent mode. Compare: how much did you have to specify up front, and how did each tool show you what it was about to change before committing to it?
