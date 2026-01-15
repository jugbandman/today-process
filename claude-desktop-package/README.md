# Today's Dump - Starter Package

Ready-to-use folder for any AI with file access.

## Quick Setup

1. **Copy this folder** to your Documents (or wherever you keep notes)
2. **Point your AI tool** at this folder
3. **Start with:** "Read my CLAUDE.md file"

**Works with:** Claude Desktop, Claude Code, Cursor, Windsurf, VS Code + Copilot, Nimbalyst, AntiGravity, or any AI with file access.

## What's Included

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Instructions AI reads to understand your system |
| `daily/today.md` | Your current day's note - command central |
| `daily/_backlog.md` | Items not for today, reviewed weekly |
| `daily/templates/` | Template for new daily notes |
| `daily/archive/` | Where old daily notes go |

## Tool-Specific Setup

### Claude Desktop (MCP)

Add to `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/this/folder"]
    }
  }
}
```

### Cursor / Windsurf

1. Open this folder as a project
2. The `.cursorrules` or AI will read CLAUDE.md automatically

### VS Code + Copilot/Continue

1. Open this folder as workspace
2. Reference CLAUDE.md in your prompts

### Other Tools (Nimbalyst, AntiGravity, etc.)

Point the tool at this folder - most will auto-read CLAUDE.md or you can reference it.

## First Steps

1. Point your AI at this folder
2. Say: "Read my CLAUDE.md file and help me get started"
3. Add a brain dump to today.md
4. Say: "Process my brain dump"

## Extending

- Add a `projects/` folder for project-specific notes
- Add a `people/` folder for contact notes
- Add a `meetings/` folder for transcripts (Granola, Otter, etc.)

AI will learn to surface context from these locations.

---

*See the main repo for full documentation: https://github.com/jugbandman/todays-dump*
