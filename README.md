# claude-cx

> Claude plans. Codex executes.

A pair of slash commands for [Claude Code](https://claude.ai/code) that activates a collaborative workflow between Claude and the [OpenAI Codex plugin](https://github.com/openai/codex-plugin-cc): Claude handles reasoning and planning, Codex handles implementation.

---

## Why

Claude and Codex have different strengths:

| | Claude | Codex |
|---|---|---|
| **Strengths** | Reasoning, planning, context, review | Fast code execution, file writes, implementation sprints |
| **Best for** | Understanding intent, writing specs, catching mistakes | Turning a clear spec into working code |

CX Mode formalizes this division. You describe what you need; Claude breaks it down into a precise spec; Codex implements it.

---

## Prerequisites

1. [Claude Code](https://claude.ai/code) installed
2. OpenAI Codex plugin installed in Claude Code:
   ```
   /plugin marketplace add openai/codex-plugin-cc
   /plugin install codex@openai-codex
   /reload-plugins
   ```
3. Codex authenticated (`/codex:setup` to verify)

---

## Installation

**macOS / Linux** — one line:
```bash
mkdir -p ~/.claude/commands && curl -sL https://raw.githubusercontent.com/WaziXuan/claude-cx/master/commands/cx.md -o ~/.claude/commands/cx.md && curl -sL https://raw.githubusercontent.com/WaziXuan/claude-cx/master/commands/cx-help.md -o ~/.claude/commands/cx-help.md
```

**Windows (PowerShell)** — one line:
```powershell
$d="$env:USERPROFILE\.claude\commands"; New-Item -ItemType Directory -Force $d | Out-Null; Invoke-WebRequest "https://raw.githubusercontent.com/WaziXuan/claude-cx/master/commands/cx.md" -OutFile "$d\cx.md"; Invoke-WebRequest "https://raw.githubusercontent.com/WaziXuan/claude-cx/master/commands/cx-help.md" -OutFile "$d\cx-help.md"
```

Then reload in Claude Code:
```
/reload-plugins
```

---

## Usage

Type `/cx` to enter CX Mode. Claude will confirm and apply the workflow to all subsequent implementation tasks in the conversation.

```
/cx-help    show the quick reference card
/cx         enter CX Mode
```

To exit, start a new conversation.

---

## How it works

Once in CX Mode, Claude applies this workflow for any implementation task:

```
1. Analyze   — understand intent, identify files, clarify constraints
2. Spec      — write a structured implementation spec
3. Delegate  — invoke codex:rescue with the spec
4. Review    — verify Codex output; intervene if needed
```

Simple tasks (single-line fixes, config edits, explanations) are handled directly by Claude without invoking Codex.

---

## Spec format

When delegating, Claude produces a spec in this format:

```
Task: [one sentence]
Files: [list of file paths]
Requirements:
  - ...
Do NOT:
  - ...
Verification: [how to confirm correctness]
```

---

## Contributing

Pull requests welcome. If you improve the delegation heuristics, the spec format, or add language-specific variants, please open a PR.

---

## License

MIT
