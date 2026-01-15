# CLAUDE.md - Today Process

This folder is set up for AI-powered daily planning with Claude Desktop.

## What This Is

The Today Process turns your morning brain dump into a structured action plan. Claude reads your notes, tracks what's been sitting, and helps you prioritize.

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
3. Ask Claude: "Process my brain dump and suggest priorities"

Claude will:
- Extract action items from your brain dump
- Categorize into Must Do / Should Do / Could Do / Waiting On
- Flag any stale items (sitting too long)
- Suggest your Top 3 priorities

### During the Day

- Check off completed tasks: `- [x]`
- Add quick notes to the Quick Notes section
- Ask Claude: "What should I focus on next?"

### End of Day

Ask Claude: "Help me wrap up the day"

Claude will:
- Summarize what got done
- Ask what to do with incomplete items (carry forward, backlog, or archive)
- Prompt for quick reflection
- Suggest tomorrow's focus

### Weekly (Sunday or Monday)

Ask Claude: "Run my weekly review"

Claude will:
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

Claude flags items sitting too long:

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
Create a `projects/` folder with subfolders for each project. Add commitments there and Claude can surface them.

### Add People
Create a `people/` folder with notes on key people. Reference commitments you owe them.

### Add Meeting Transcripts
If using Granola or Otter, save transcripts to a `meetings/` folder. Ask Claude to extract action items.

---

*This system works because Claude can read and write your files directly. That's the unlock.*
