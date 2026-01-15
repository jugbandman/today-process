# Today Process - Claude Desktop Package

Ready-to-use folder for Claude Desktop with MCP filesystem access.

## Quick Setup

1. **Copy this folder** to your Documents (or wherever you keep notes)
2. **Configure Claude Desktop** to access this folder via MCP
3. **Open Claude Desktop** and start with: "Read my CLAUDE.md file"

## What's Included

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Instructions Claude reads to understand your system |
| `daily/today.md` | Your current day's note - command central |
| `daily/_backlog.md` | Items not for today, reviewed weekly |
| `daily/templates/` | Template for new daily notes |
| `daily/archive/` | Where old daily notes go |

## MCP Configuration

Add to your Claude Desktop config (`~/Library/Application Support/Claude/claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "/path/to/this/folder"
      ]
    }
  }
}
```

Replace `/path/to/this/folder` with where you put this folder.

## First Steps

1. Open Claude Desktop
2. Say: "Read my CLAUDE.md file and help me get started"
3. Add a brain dump to today.md
4. Say: "Process my brain dump"

## Extending

- Add a `projects/` folder for project-specific notes
- Add a `people/` folder for contact notes
- Add a `meetings/` folder for transcripts (Granola, Otter, etc.)

Claude will learn to surface context from these locations.

---

*See the main repo for full documentation: https://github.com/jugbandman/today-process*
