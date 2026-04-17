Display the following CX Mode reference card to the user. Do not take any other action.

---

## CX Mode — Quick Reference

**What it is:** Claude reasons and plans; Codex (GPT-4o / GPT-5) writes and executes the code.

### Commands

| Command | Action |
|---------|--------|
| `/cx` | Enter CX Mode |
| `/cx-help` | Show this reference card |
| Start a new conversation | Exit CX Mode |

### Workflow

```
You describe the task
      ↓
Claude analyzes + writes a spec
      ↓
Codex implements (file writes, execution)
      ↓
Claude reviews the output
```

### Delegation rules

| Task type | Handled by |
|-----------|------------|
| New feature / module | Codex |
| Changes across 3+ files | Codex |
| Greenfield / scaffolding | Codex |
| Complex algorithm | Codex |
| Single-line bug fix | Claude |
| Config / docs change | Claude |
| Code explanation | Claude |
| "You do it" | Claude |

### Spec format (what Claude sends to Codex)

```
Task: [one sentence]
Files: [paths]
Requirements:
  - ...
Do NOT:
  - ...
Verification: [how to confirm]
```
