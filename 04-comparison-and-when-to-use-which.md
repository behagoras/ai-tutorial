# Lesson 4 — Comparison & When to Use Which

**After this lesson you'll be able to:** pick the right tool for a given job from a single reference table and a short decision guide, and know how to combine both in one workflow.

## Consolidated feature comparison

| Feature | Claude Code | Cursor |
|---|---|---|
| Surface | Terminal-native CLI (+ IDE extensions) | Standalone editor (VS Code fork) |
| Autocomplete-as-you-type | Not supported | Tab completion |
| Scoped inline edit | Via conversational instruction, no dedicated shortcut | Inline edit (Cmd/Ctrl+K family — check current docs for exact shortcut) |
| Multi-file agentic edits | Core mode | Composer / Agent mode |
| Plan-before-edit | Plan mode | Custom modes (approximate) |
| Project memory file | CLAUDE.md | .cursor/rules |
| Explicit file context | `@`-file references | `@`-symbols (`@files`, `@docs`, `@web`) |
| Codebase-wide awareness | Live tool-driven exploration each session | Pre-built codebase index |
| Parallel/isolated agent work | Subagents | No direct equivalent; background agents cover a different need |
| External tools/data | MCP | MCP (also supported) |
| Reusable saved prompts | Slash commands | No direct equivalent |
| Lifecycle automation hooks | Hooks | No direct equivalent |
| CI / unattended scripting | Headless mode — first-class | Not its design center |
| Autonomy dial | Permission modes | Agent auto-run/auto-accept settings |
| Named custom workflow modes | Not a general system | Custom modes |
| Run task without blocking editor | Separate terminal / async headless run | Background agents |
| Integrated terminal commands | Native (it *is* terminal-native) | Integrated terminal (VS Code-based) |

## Decision guide

- **Big, cross-file refactor:** Claude Code — agentic multi-file editing plus plan mode to review the approach before it touches anything, and it can run your tests/build as it goes to self-check.
- **Quick, scoped inline edit while you're mid-flow:** Cursor — Tab completion and inline edit are built for exactly this, with lower latency than a full conversational round trip.
- **Terminal-heavy work (scripting, CI, git-heavy workflows, unattended runs):** Claude Code — it lives there natively, including headless mode for non-interactive use.
- **Exploring an unfamiliar repo:** either works; Cursor's codebase indexing gives fast retrieval-backed answers inside the editor you're already reading code in, while Claude Code's live exploration is equally capable and pairs well if you're going to immediately ask it to also make a change based on what it finds.
- **Need saved, reusable, team-shared workflows (checklists, routines):** Claude Code — slash commands and hooks are built for this; check current Cursor docs, as this gap may narrow over time.
- **Need to keep working while a big task runs elsewhere:** Cursor's background agents, or Claude Code kicked off in a separate terminal/async headless run.

## Combining both in one workflow

They're not mutually exclusive — a natural pairing:

- Use Cursor as your daily editor for the moment-to-moment loop (Tab completion, inline edits, reading code) — you're in an editor either way, so let it carry the load AI-editors are built for.
- Reach for Claude Code in a terminal alongside it for anything that's really an agentic *task* rather than an edit: a multi-file refactor, a scripted/automated step, a CI-bound job, or something you want to hand off and not sit in front of.
- Keep both a `CLAUDE.md` and `.cursor/rules` in the repo with the same core conventions (even duplicated) so whichever tool you (or a teammate) reach for that day has the same standing context.
- If a task starts in one and needs the other's strength (e.g., you planned a refactor in Claude Code's plan mode, now want to hand-tune a few spots inline), just open the other tool on the same working tree — they operate on the same files/git state, there's no lock-in.

## Try it

Take a real task currently on your plate. Before starting, decide which tool fits using the guide above, and write one sentence saying why. Do the task in that tool. Then note: did you at any point wish you had the other tool's specific strength (autocomplete, headless scripting, background running)? That instinct is the real signal for how you'll split your work between the two going forward.
