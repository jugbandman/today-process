# Today Process

An AI-powered daily workflow that turns your morning brain dump into a structured action plan.

**The unlock:** Claude (Desktop or Code) connected to your local files. AI that can read your notes, see what's been sitting, and write your daily plan.

---

## The Problem

You wake up with 47 things swirling in your head. Yesterday's unfinished tasks. Today's meetings. That thing you promised someone. Random worries.

Traditional approaches fail:
- **Todo apps** require manual entry (friction)
- **Calendar apps** show meetings, not context
- **Your brain** drops things between days
- **ChatGPT/Claude web** can't see your files (no memory)

The cognitive load of "figuring out what to do" consumes energy that should go toward *doing*.

## The Solution

**Connect Claude to your files.** Using Claude Desktop (MCP) or Claude Code, AI gets direct access to your notes folder. It can:

- Read yesterday's note and carry forward incomplete tasks
- See what's been sitting for 3 days and flag it
- Write directly to today.md
- Track your backlog and prompt weekly reviews

**Talk, don't type.** Do a 2-3 minute voice brain dump each morning. Say everything on your mind.

**AI extracts and structures.** Claude reads your transcript and:
- Extracts action items
- Categorizes by priority (Must/Should/Could/Waiting)
- Flags stale items ("This has been in Must Do for 3 days")
- Suggests your Top 3 focus areas

**Work from clarity.** Your `today.md` becomes command central.

---

## The Unlock: Claude + Your Files

This isn't copy/paste to a chatbot. Claude has **direct file access**:

| Capability | What It Means |
|------------|---------------|
| **Read** | Sees yesterday's note, your backlog, project files |
| **Write** | Creates today.md, updates backlog, archives old notes |
| **Track** | Knows what's been sitting, what moved, what's stale |
| **Remind** | "This urgent task has been here 3 days" |

Two ways to connect:

| Tool | Best For | Setup Time |
|------|----------|------------|
| **Claude Desktop + MCP** | Non-coders, simple setup | 30 min |
| **Claude Code** | Power users, full automation | 1-2 hours |

See [Setup Guide](docs/setup-guide.md) for both paths.

---

## Quick Start

### Option 1: Just Try the Methodology (No Setup)

1. Open [claude.ai](https://claude.ai)
2. Paste this prompt:

```
Here's my morning brain dump. Please:
1. Extract all action items
2. Categorize as: Must Do Today / Should Do Today / Could Do If Time / Waiting On Others
3. Flag anything that sounds urgent
4. Suggest my Top 3 priorities

Brain dump:
[Paste your stream-of-consciousness here]
```

3. See the value. Then set up file access for the full experience.

### Option 2: Full Setup (Recommended)

See [Setup Guide](docs/setup-guide.md) for:
- Claude Desktop with MCP filesystem access
- Claude Code with skills
- Backlog tracking and weekly reviews
- Staleness alerts

---

## What You Get

### Daily Note (`today.md`)

```markdown
# Today: Monday, January 14, 2026

## Top 3 Priorities
1. [AI-suggested based on deadlines and staleness]
2. [Your most important work]
3. [Key commitment]

## Stale Items ⚠️
<!-- AI surfaces these automatically -->
- "Send proposal to Client A" - in Must Do for 3 days
- "Follow up with Bob" - marked urgent on Friday

## Brain Dump
[Your raw morning thoughts - AI processes this]

## Tasks

### Must Do Today
- [ ] Hard deadlines, critical items

### Should Do Today
- [ ] Important but timing flexible

### Could Do If Time
- [ ] Nice to have

### Waiting On Others
- [ ] Blocked items with context

## End of Day Reflection
**What got done:**
**What blocked progress:**
**Tomorrow's focus:**
```

### Backlog (`_backlog.md`)

A separate file for someday/maybe items:

```markdown
# Backlog

## To Review
<!-- Items pushed here get reviewed weekly -->
- [ ] Redesign the onboarding flow (pushed 2026-01-10)
- [ ] Research new CRM options (pushed 2026-01-08)

## Someday/Maybe
- [ ] Learn Spanish
- [ ] Build personal website

## Archived
<!-- Decided not to do -->
- [x] Old project idea (archived 2026-01-05: no longer relevant)
```

### Weekly Review

Every Sunday (or your chosen day), Claude prompts:

```
It's weekly review time. Let me check your backlog...

## Stale in Backlog (sitting 7+ days)
- "Research CRM options" - pushed here Jan 8 (6 days ago)
- "Redesign onboarding" - pushed here Jan 10 (4 days ago)

## Recurring Incomplete
- "Exercise" appeared in Could Do 4 of 5 days, never completed

## Questions
1. "Research CRM options" - pull forward to this week, or archive?
2. "Redesign onboarding" - still relevant?
3. Want to schedule "Exercise" as a Must Do?
```

---

## Staleness Tracking

Claude tracks how long items sit:

| Duration | What Happens |
|----------|--------------|
| **2 days in Must Do** | Flagged in Stale Items section |
| **3 days in Should Do** | Suggested to demote or address |
| **7 days in backlog** | Prompted in weekly review |
| **Recurring skip** | "You've skipped this 4 times - archive it?" |

This prevents the "infinite todo list" problem.

---

## Setup Paths

| Path | Who It's For | Guide |
|------|--------------|-------|
| **Claude Desktop + MCP** | Want it simple, comfortable with apps | [Setup Guide](docs/setup-guide.md#claude-desktop) |
| **Claude Code** | Want full automation, comfortable with terminal | [Setup Guide](docs/setup-guide.md#claude-code) |
| **Obsidian + Either** | Already use Obsidian | [Setup Guide](docs/setup-guide.md#obsidian-integration) |

---

## Templates

Ready to copy to your setup:

| Template | Purpose |
|----------|---------|
| [daily-template.md](templates/daily-template.md) | Daily note structure |
| [backlog-template.md](templates/backlog-template.md) | Backlog with Done section |
| [start-my-day.skill.md](templates/start-my-day.skill.md) | Morning routine + Monday planning |
| [end-of-day.skill.md](templates/end-of-day.skill.md) | Daily wrap up + reflections |
| [weekly-review.skill.md](templates/weekly-review.skill.md) | Weekly backlog cleanup |
| [claude-desktop-config.json](templates/claude-desktop-config.json) | MCP filesystem setup |

### Skills Quick Install (Claude Code)

```bash
# Create skill folders
mkdir -p ~/.claude/skills/start-my-day
mkdir -p ~/.claude/skills/end-of-day
mkdir -p ~/.claude/skills/weekly-review

# Download skills (replace with actual paths after cloning)
# Copy templates/*.skill.md to ~/.claude/skills/[name]/SKILL.md
# Edit paths in each skill to match your setup
```

---

## How It Works

```
Morning Brain Dump
       ↓
Claude reads brain dump + yesterday's note + backlog
       ↓
Extracts tasks, flags stale items, suggests priorities
       ↓
Writes to today.md (you confirm/adjust)
       ↓
Work your day
       ↓
End of day: reflection + push incomplete to tomorrow/backlog
       ↓
Weekly: backlog review, clean up stale items
```

---

## FAQ

**Why Claude Desktop/Code instead of ChatGPT?**
MCP filesystem access. Claude can read/write your actual files. ChatGPT can't (yet).

**Do I need Obsidian?**
No. Any folder with markdown files works. Obsidian adds nice features (linking, plugins) but isn't required.

**What if I skip a day?**
Claude sees the gap. It'll carry forward incomplete items and note what was missed.

**Can I use this with my existing task manager?**
Yes. This is a *daily planning layer*, not a replacement for Todoist/Things/etc. Use it to decide what matters today.

**What about mobile?**
Brain dump capture works on mobile (voice memos). Full Claude integration is desktop for now.

---

## Examples

See a real implementation: [examples/implementation-example.md](examples/implementation-example.md)

---

## Contributing

PRs welcome:
- Integration guides for other tools
- Improvements to templates
- Your implementation as an example

---

## License

MIT - Use however you want.

---

*Created by [Andy Carlson](https://github.com/jugbandman). Built with Claude.*
