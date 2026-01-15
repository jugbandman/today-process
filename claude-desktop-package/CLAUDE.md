# CLAUDE.md - Today's Dump

This folder is set up for AI-powered daily planning.

## What This Is

Today's Dump turns your morning brain dump into a structured action plan. AI reads your notes, tracks what's been sitting, and helps you prioritize.

**Works with:** Claude Desktop, Claude Code, Cursor, Windsurf, VS Code + Copilot, Nimbalyst, AntiGravity, or any AI with file access.

## Folder Structure

```
daily/
├── today.md              # Current day's note (your command center)
├── _backlog.md           # Items not for today, reviewed weekly
├── templates/
│   └── daily-template.md # Template for new daily notes
└── archive/
    └── YYYY/MM-month/    # Previous days' notes
```

## How to Use

### Morning Routine

1. Open `daily/today.md`
2. Add your brain dump to the Brain Dump section (voice transcript or typed thoughts)
3. Ask AI: "Process my brain dump and suggest priorities"

AI will:
- Extract action items from your brain dump
- Categorize into Must Do / Should Do / Could Do / Waiting On
- Flag any stale items (sitting too long)
- Suggest your Top 3 priorities

### During the Day

- Check off completed tasks: `- [x]`
- Add quick notes to the Quick Notes section
- Ask AI: "What should I focus on next?"

### End of Day

Ask AI: "Help me wrap up the day"

AI will:
- Summarize what got done
- Ask what to do with incomplete items (carry forward, backlog, or archive)
- Prompt for quick reflection
- Suggest tomorrow's focus

### Weekly (Sunday or Monday)

Ask AI: "Run my weekly review"

AI will:
- Archive old completed items from backlog
- Flag items sitting too long
- Report patterns ("You've skipped Exercise 4 times")
- Help you decide what to keep, archive, or prioritize

## Task Categories

- **Must Do Today** - Hard deadlines, critical items
- **Should Do Today** - Important but timing flexible
- **Could Do If Time** - Nice to have
- **Waiting On Others** - Blocked, tracking for follow-up

## Staleness Tracking

AI flags items sitting too long:

| Where | How Long | What Happens |
|-------|----------|--------------|
| Must Do | 2+ days | Flagged as stale |
| Should Do | 3+ days | Suggest promote or demote |
| Backlog | 7+ days | Review in weekly |

## Commands You Can Use

- "Process my brain dump"
- "What's stale?"
- "Suggest my Top 3"
- "Help me wrap up the day"
- "Run my weekly review"
- "What do I owe [person]?"
- "Push [task] to backlog"

## Extending This System

### Add Projects
Create a `projects/` folder with subfolders for each project. Add commitments there and AI can surface them.

### Add People
Create a `people/` folder with notes on key people. Reference commitments you owe them.

### Add Meeting Transcripts
If using Granola or Otter, save transcripts to a `meetings/` folder. Ask AI to extract action items.

---

*This system works because AI can read and write your files directly. That's the unlock.*
