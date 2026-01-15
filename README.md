# Today's Dump

An AI-powered daily workflow that turns your morning brain dump into a structured action plan.

**The unlock:** AI connected to your local files. Any AI that can read your notes, see what's been sitting, and write your daily plan.

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

**Connect AI to your files.** Using any AI tool with file access, you get direct access to your notes folder. It can:

- Read yesterday's note and carry forward incomplete tasks
- See what's been sitting for 3 days and flag it
- Write directly to today.md
- Track your backlog and prompt weekly reviews

**Talk, don't type.** Do a 2-3 minute voice brain dump each morning. Say everything on your mind.

**AI extracts and structures.** Your AI reads your transcript and:
- Extracts action items
- Categorizes by priority (Must/Should/Could/Waiting)
- Flags stale items ("This has been in Must Do for 3 days")
- Suggests your Top 3 focus areas

**Work from clarity.** Your `today.md` becomes command central.

---

## The Unlock: AI + Your Files

This isn't copy/paste to a chatbot. AI has **direct file access**:

| Capability | What It Means |
|------------|---------------|
| **Read** | Sees yesterday's note, your backlog, project files |
| **Write** | Creates today.md, updates backlog, archives old notes |
| **Track** | Knows what's been sitting, what moved, what's stale |
| **Remind** | "This urgent task has been here 3 days" |

## Compatible Tools

Today's Dump works with any AI that can access your local files:

| Tool | Type | File Access |
|------|------|-------------|
| **Claude Desktop** | Chat app | MCP filesystem |
| **Claude Code** | CLI/IDE | Direct + skills |
| **Claude CoWork** | Collaborative | Workspace files |
| **Cursor** | IDE | Project files |
| **Windsurf** | IDE | Project files |
| **VS Code + Copilot/Continue** | IDE | Workspace |
| **Nimbalyst** | Automation | Connected folders |
| **AntiGravity** | Agent | File system access |

**The pattern is the same:** Point the AI at your notes folder, give it a CLAUDE.md (or equivalent instructions file), and it works.

See [Setup Guide](docs/setup-guide.md) for tool-specific setup.

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

Every Sunday (or your chosen day), AI prompts:

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

AI tracks how long items sit:

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
| **Claude Desktop** | Simple chat interface | [Setup Guide](docs/setup-guide.md#claude-desktop) |
| **Claude Code** | Terminal power users | [Setup Guide](docs/setup-guide.md#claude-code) |
| **Cursor/Windsurf** | IDE-native workflow | [Setup Guide](docs/setup-guide.md#ide-setup) |
| **Other AI Tools** | Nimbalyst, AntiGravity, etc. | [Setup Guide](docs/setup-guide.md#other-tools) |

---

## Quick Start Options

### Option A: Any AI Tool (Easiest)

1. **Download the zip:** [todays-dump-starter.zip](todays-dump-starter.zip)
2. **Extract** to your Documents folder
3. **Point your AI** at the folder (MCP, workspace, project folder)
4. **Say:** "Read my CLAUDE.md and help me get started"

The zip includes everything ready to go - just extract and connect. Works with Claude Desktop, Cursor, Windsurf, Nimbalyst, AntiGravity, or any AI with file access.

### Option B: Claude Code (Full Automation with Skills)

```bash
# Clone the repo
git clone https://github.com/jugbandman/today-process.git

# Create skill folders
mkdir -p ~/.claude/skills/start-my-day
mkdir -p ~/.claude/skills/end-of-day
mkdir -p ~/.claude/skills/weekly-review

# Copy skills
cp today-process/templates/start-my-day.skill.md ~/.claude/skills/start-my-day/SKILL.md
cp today-process/templates/end-of-day.skill.md ~/.claude/skills/end-of-day/SKILL.md
cp today-process/templates/weekly-review.skill.md ~/.claude/skills/weekly-review/SKILL.md

# Edit paths in each skill to match your vault location
```

Then use `/start-my-day`, `/end-of-day`, `/weekly-review` commands.

---

## What's In This Repo

### Templates (Copy These)

| File | Purpose |
|------|---------|
| [daily-template.md](templates/daily-template.md) | Daily note structure |
| [backlog-template.md](templates/backlog-template.md) | Backlog with Done section |
| [start-my-day.skill.md](templates/start-my-day.skill.md) | Morning routine with adaptive onboarding |
| [end-of-day.skill.md](templates/end-of-day.skill.md) | Daily wrap up with reflections |
| [weekly-review.skill.md](templates/weekly-review.skill.md) | Weekly backlog cleanup |
| [claude-desktop-config.json](templates/claude-desktop-config.json) | MCP filesystem config |
| [extensions/time-tracking.md](templates/extensions/time-tracking.md) | Client time tracking for invoicing |

### Documentation

| File | Purpose |
|------|---------|
| [docs/setup-guide.md](docs/setup-guide.md) | Full setup for Desktop and Code |
| [docs/extensions.md](docs/extensions.md) | Optional features (calendar, time blocking) |
| [docs/cheat-sheet.md](docs/cheat-sheet.md) | Quick reference |

### Examples

| File | Purpose |
|------|---------|
| [examples/what-you-can-do.md](examples/what-you-can-do.md) | Real scenarios and AI responses |
| [examples/implementation-example.md](examples/implementation-example.md) | Complete implementation walkthrough |

### Claude Desktop Package

| File | Purpose |
|------|---------|
| [todays-dump-starter.zip](todays-dump-starter.zip) | Ready-to-use folder with all files |
| [claude-desktop-package/](claude-desktop-package/) | Unzipped version |

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

## Intelligent Features

### In-Progress Mode

Run `/start-my-day` multiple times - it won't recreate your file. If today.md exists for today, it:
- Scans for new brain dump content
- Checks for completed tasks
- Looks for new meeting transcripts
- Offers to update your priorities

### Monday Planning

On Mondays, `/start-my-day` automatically adds weekly planning:
- Reviews last week's completed and carried items
- Checks backlog for stale items
- Suggests weekly priorities before daily

### Adaptive Onboarding

Skills learn your workflow over time:

**First run:** Asks setup questions (paths, features, preferences)
**Ongoing:** May ask 1-2 refinement questions based on patterns
**Pattern recognition:** "You've skipped Exercise 4 times - different approach?"
**User control:** Say "stop asking" to disable suggestions

Configuration saved to `.today-process-config.md` - edit anytime.

---

## What's Extendable

| Component | How to Extend |
|-----------|---------------|
| **Task categories** | Edit template: MoSCoW, Eisenhower, or custom |
| **Staleness thresholds** | Edit skill: change 2-day, 3-day, 7-day defaults |
| **Client time tracking** | Add `_timelog.md` per client for invoicing (see [time-tracking.md](templates/extensions/time-tracking.md)) |
| **Meeting integration** | Add Granola, Otter, or custom transcript folder |
| **Project surfacing** | Add `projects/` folder with MOCs |
| **People tracking** | Add `people/` folder with commitments |
| **Calendar** | Connect via MCP for time blocking |
| **Reflections** | Enable/disable in config |
| **Questions** | Disable adaptive questions anytime |

### Adding Your Own Features

The skills are markdown files - edit them directly:

```markdown
## My Custom Phase

### Phase X: Check Email
Scan inbox for urgent items, add to Must Do if needed.
```

Skills live at `~/.claude/skills/{name}/SKILL.md` (Claude Code) or are embedded in your instructions file (CLAUDE.md, .cursorrules, etc.).

---

## FAQ

**Why not just ChatGPT web?**
File access. Today's Dump needs AI that can read/write your actual files. ChatGPT web can't (yet). Use Claude Desktop, Cursor, Windsurf, or any AI tool with local file access.

**Do I need Obsidian?**
No. Any folder with markdown files works. Obsidian adds nice features (linking, plugins) but isn't required.

**What if I skip a day?**
AI sees the gap. It'll carry forward incomplete items and note what was missed.

**Can I use this with my existing task manager?**
Yes. This is a *daily planning layer*, not a replacement for Todoist/Things/etc. Use it to decide what matters today.

**What about mobile?**
Brain dump capture works on mobile (voice memos). Full AI integration is desktop for now.

**How do I stop the setup questions?**
Say "stop asking setup questions" - it saves your preference and only asks when you run `/configure-workflow`.

**Can I customize everything?**
Yes. Skills are markdown files. Edit paths, thresholds, categories, phases - anything you want.

---

## Examples

See real scenarios and AI responses: [examples/what-you-can-do.md](examples/what-you-can-do.md)

See a complete implementation: [examples/implementation-example.md](examples/implementation-example.md)

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

*Created by [Andy Carlson](https://github.com/jugbandman). Works with any AI that can access your files.*
