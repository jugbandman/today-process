# Today Process

An AI-powered daily workflow that turns your morning brain dump into a structured action plan.

---

## The Problem

You wake up with 47 things swirling in your head. Yesterday's unfinished tasks. Today's meetings. That thing you promised someone. Random worries.

Traditional approaches fail:
- **Todo apps** require manual entry (friction)
- **Calendar apps** show meetings, not context
- **Your brain** drops things between days

The cognitive load of "figuring out what to do" consumes energy that should go toward *doing*.

## The Solution

**Talk, don't type.** Do a 2-3 minute voice brain dump each morning. Say everything on your mind - don't organize, just dump.

**AI extracts and structures.** Claude reads your transcript and:
- Extracts action items
- Categorizes by priority (Must/Should/Could/Waiting)
- Surfaces commitments you owe people
- Suggests your Top 3 focus areas

**Work from clarity.** Your `today.md` becomes command central - one file with everything you need.

---

## Quick Start (5 minutes)

### Option 1: Just Try It (No Setup)

1. Open [claude.ai](https://claude.ai)
2. Paste this prompt with your own brain dump:

```
Here's my morning brain dump. Please:
1. Extract all action items
2. Categorize as: Must Do Today / Should Do Today / Could Do If Time / Waiting On Others
3. Suggest my Top 3 priorities for today

Brain dump:
[Paste your stream-of-consciousness thoughts here - what you need to do,
what's worrying you, meetings, deadlines, random stuff - don't organize, just dump]
```

3. Review Claude's structured output
4. That's the Today Process. Everything else is automation.

### Option 2: Full Setup

See the [Setup Guide](docs/setup-guide.md) for:
- Obsidian + Claude Code integration
- Automated `/start-my-day` skill
- Meeting transcript processing
- Commitment tracking across projects

---

## What You Get

### Daily Note Structure

```markdown
# Today: Monday, January 14, 2026

## Top 3 Priorities
1. [AI-suggested based on deadlines and context]
2. [Your most important work]
3. [Key commitment]

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

### Morning Routine (5-10 min)

| Step | Time | What Happens |
|------|------|--------------|
| Brain dump | 2-3 min | Talk through everything on your mind |
| AI processing | 1 min | Run `/start-my-day` or paste to Claude |
| Review | 2-3 min | Confirm priorities, adjust categories |

---

## Setup Paths

| Path | Who It's For | Time | Guide |
|------|--------------|------|-------|
| **Minimal** | Try it first | 5 min | Copy/paste to claude.ai |
| **Obsidian** | Note-takers | 1 hour | [Setup Guide](docs/setup-guide.md) |
| **Full Automation** | Power users | 2-3 hours | [Setup Guide](docs/setup-guide.md) + Claude Code |

---

## Templates

Ready to copy:

| Template | Purpose |
|----------|---------|
| [daily-template.md](templates/daily-template.md) | Daily note structure |
| [start-my-day.skill.md](templates/start-my-day.skill.md) | Claude Code skill |
| [CLAUDE.md.example](templates/CLAUDE.md.example) | Vault configuration |

---

## How It Works

```
Voice Brain Dump          AI Processing              Structured Day
     │                         │                          │
     ▼                         ▼                          ▼
"Need to call John,    →   Extracts tasks,      →    today.md with
 meeting at 2pm,           categorizes,              clear priorities
 worried about             suggests Top 3            and next actions
 Friday deadline..."
```

The key insight: **The methodology is universal. The implementation is personal.**

- Core loop works with any folder + any AI
- Obsidian adds linking and plugins
- Claude Code adds automation
- Pick your level of tooling

---

## Examples

See how one person implemented it: [examples/implementation-example.md](examples/implementation-example.md)

Includes:
- Folder structure decisions
- Meeting transcript integration
- Client/project commitment tracking
- What to customize for your context

---

## FAQ

**Do I need Obsidian?**
No. Any folder with markdown files works. Obsidian just adds nice features.

**Do I need Claude Code?**
No. Copy/paste to claude.ai works fine. Claude Code automates it.

**What about existing todo systems?**
This doesn't replace your task manager. It's a *daily planning layer* that feeds into whatever system you use.

**How is this different from Bullet Journal / GTD / etc?**
Those require you to do the categorization. This uses AI to do the cognitive work of extracting and prioritizing.

**What if I miss a day?**
Just start fresh. Check yesterday's archive for carried items.

---

## Contributing

Found a better way to do something? PRs welcome.

- Improve the templates
- Add integration guides (Notion, Logseq, etc.)
- Share your implementation as an example

---

## License

MIT - Use it however you want.

---

*Created by [Andy Carlson](https://github.com/jugbandman). Built with Claude.*
