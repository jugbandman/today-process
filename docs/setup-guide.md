# Setup Guide

Connect Claude to your files for the full Today Process experience.

---

## Choose Your Path

| Path | Best For | Setup Time | What You Get |
|------|----------|------------|--------------|
| **Claude Desktop + MCP** | Non-coders, simple setup | 30 min | File read/write, manual commands |
| **Claude Code** | Power users, developers | 1-2 hours | Full automation, skills, git integration |
| **Just Obsidian** | Want to try first | 15 min | Copy/paste workflow (no file access) |

**The unlock is file access.** Both Claude Desktop and Claude Code can read/write your notes directly. That's what makes staleness tracking and backlog management possible.

---

# Path A: Claude Desktop + MCP (Recommended for Most)

## A1: Install Claude Desktop

1. Download from [claude.ai/download](https://claude.ai/download)
2. Install and sign in with your Anthropic account

## A2: Create Your Notes Folder

Create a folder for your daily notes:

```
~/Documents/today-process/
├── daily/
│   ├── today.md
│   └── archive/
├── _backlog.md
└── templates/
    └── daily-template.md
```

Or use an existing Obsidian vault - just note the path.

## A3: Configure MCP Filesystem Access

Claude Desktop uses MCP (Model Context Protocol) to access local files.

1. Open Claude Desktop settings
2. Navigate to Developer settings
3. Edit the MCP configuration file (or create it):

**Mac:** `~/Library/Application Support/Claude/claude_desktop_config.json`
**Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

Add this configuration:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "/Users/YOUR_USERNAME/Documents/today-process"
      ]
    }
  }
}
```

**Replace `/Users/YOUR_USERNAME/Documents/today-process`** with your actual folder path.

See [templates/claude-desktop-config.json](../templates/claude-desktop-config.json) for the full template.

## A4: Restart Claude Desktop

Quit and reopen Claude Desktop. You should see a hammer icon indicating MCP tools are available.

## A5: Test File Access

In Claude Desktop, type:

```
Read the file at daily/today.md and tell me what's there
```

If Claude reads your file, you're connected.

## A6: Copy Templates

Copy these to your notes folder:
- [templates/daily-template.md](../templates/daily-template.md) → `templates/`
- [templates/backlog-template.md](../templates/backlog-template.md) → rename to `_backlog.md`

## A7: Your Daily Workflow

**Morning:**
```
Start my day. Read yesterday's note, check the backlog, and help me
create today.md. Here's my brain dump: [paste or type your thoughts]
```

**End of day:**
```
Review today.md. What didn't get done? Help me decide:
carry forward to tomorrow, push to backlog, or archive?
```

**Weekly (Sunday or Monday):**
```
Weekly review. Check my backlog for stale items, look at what I've
been skipping repeatedly, and help me clean up.
```

---

# Path B: Claude Code (Power Users)

## B1: Install Prerequisites

```bash
# Node.js (if not installed)
brew install node  # Mac
# or download from nodejs.org

# Claude Code
npm install -g @anthropic-ai/claude-code

# Authenticate
claude login
```

## B2: Create Notes Folder

Same as A2 above, or use existing Obsidian vault.

## B3: Create CLAUDE.md

Add `CLAUDE.md` to your notes folder root:

```markdown
# Today Process

## Folder Structure
- `daily/today.md` - Current day
- `daily/archive/YYYY/MM-month/` - Previous days
- `_backlog.md` - Someday/maybe items
- `templates/` - Note templates

## Commands
- `/start-my-day` - Morning routine with staleness check
- `/weekly-review` - Backlog cleanup and planning
- `/end-of-day` - Reflection and carry forward
```

## B4: Install Skills

```bash
mkdir -p ~/.claude/skills/start-my-day
mkdir -p ~/.claude/skills/weekly-review
```

Copy skill files:
- [templates/start-my-day.skill.md](../templates/start-my-day.skill.md) → `~/.claude/skills/start-my-day/SKILL.md`
- [templates/weekly-review.skill.md](../templates/weekly-review.skill.md) → `~/.claude/skills/weekly-review/SKILL.md`

**Edit the paths in each skill** to match your notes folder.

## B5: Copy Templates

Same as A6 above.

## B6: Test It

```bash
cd ~/Documents/today-process  # or your folder
claude

# In Claude Code:
/start-my-day
```

## B7: Your Daily Workflow

**Morning:**
```
/start-my-day

# Then paste your brain dump when prompted
```

**End of day:**
```
/end-of-day
```

**Weekly:**
```
/weekly-review
```

---

# Path C: Obsidian Integration

Works with either Claude Desktop or Claude Code.

## C1: Point to Your Vault

In your MCP config or CLAUDE.md, use your Obsidian vault path:

```
/Users/YOUR_USERNAME/Documents/Obsidian Vault
```

## C2: Folder Structure

Add to your existing vault:

```
your-vault/
├── daily/           # Or 01-daily, or whatever you use
│   ├── today.md
│   ├── archive/
│   └── templates/
│       └── daily-template.md
└── _backlog.md      # Top-level backlog
```

## C3: Optional Plugins

- **Templater** - For date variables in templates
- **Calendar** - Visual navigation of daily notes
- **Dataview** - Query your backlog and tasks
- **Granola Sync** - Auto-import meeting transcripts

## C4: Optional Granola

[Granola](https://granola.so) transcribes meetings automatically:

1. Install Granola
2. Install Obsidian Granola Sync plugin
3. Configure to save transcripts to `Granola/` folder
4. Add to your morning routine: "Process any new Granola transcripts"

---

# Voice Capture Setup

Get your thoughts into text:

| Method | Setup |
|--------|-------|
| **iPhone Voice Memos** | Record → transcribe (iOS 18+) → paste |
| **Mac Dictation** | System Settings → Keyboard → Dictation ON. Press Cmd+Cmd to activate |
| **Whisper** | `brew install whisper` then `whisper audio.m4a --output_format txt` |
| **Google Docs** | Open doc → Tools → Voice Typing |
| **Otter.ai** | Download app, record, copy transcript |

---

# Staleness Tracking

Claude tracks how long items sit. This requires file access (MCP or Claude Code).

## How It Works

When Claude reads your notes, it checks:

1. **Archive dates** - When was the last daily note archived?
2. **Task history** - Has this exact task text appeared before?
3. **Backlog timestamps** - When was each item pushed to backlog?

## What Gets Flagged

| Condition | Alert |
|-----------|-------|
| Must Do item for 2+ days | "⚠️ This has been urgent for 3 days" |
| Should Do item for 3+ days | "Consider demoting or addressing" |
| Backlog item for 7+ days | "Stale - review in weekly" |
| Same item skipped 4+ times | "You keep skipping this - archive?" |

## Enabling Timestamps

For best tracking, include dates when pushing to backlog:

```markdown
- [ ] Research CRM options (pushed 2026-01-08)
```

The skills do this automatically.

---

# Weekly Review Setup

## Trigger

Choose your day:
- **Sunday evening** - Plan the week ahead
- **Monday morning** - Start fresh
- **Friday afternoon** - Close out the week

## What Gets Reviewed

1. **Stale backlog items** (7+ days)
2. **Recurring incomplete tasks** (appeared 3+ times, never done)
3. **Overdue items** (had a deadline that passed)
4. **Waiting On items** (anything sitting too long)

## Actions

For each item, decide:
- **Pull forward** - Move to this week's priorities
- **Keep in backlog** - Still relevant, not urgent
- **Archive** - No longer relevant
- **Delete** - Was never going to happen

---

# Troubleshooting

**Claude Desktop can't access files**
- Check MCP config path is correct
- Restart Claude Desktop after config changes
- Look for hammer icon (indicates MCP tools loaded)

**Claude Code skills not working**
- Verify skill path: `~/.claude/skills/skill-name/SKILL.md`
- Check skill has correct frontmatter (name, description)
- Ensure paths in skill match your folder structure

**Staleness not tracking**
- Make sure Claude can read archive folder
- Include dates when pushing items to backlog
- Use consistent task text (don't rephrase every day)

**Weekly review not prompting**
- It doesn't auto-trigger - you run it manually
- Try: "It's weekly review time" or `/weekly-review`

---

# Next Steps

1. **Start simple** - Just brain dump + task extraction for week 1
2. **Add backlog** - Week 2, start pushing deferred items
3. **Add weekly review** - Week 3, make it a habit
4. **Customize** - Adjust categories, add sections, make it yours

---

*Cheat sheet: [docs/cheat-sheet.md](cheat-sheet.md)*
