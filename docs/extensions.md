# Extensions

Optional add-ons to the core Today Process. Pick what fits your workflow.

---

## Overview

| Extension | What It Does | Complexity |
|-----------|--------------|------------|
| **Calendar Integration** | Create time blocks, link to today.md | Medium |
| **Time Blocking** | Schedule focus blocks for priorities | Low |
| **Meeting Prep** | Auto-generate prep notes before meetings | Low |
| **Weekly Planning** | Monday planning session | Low |
| **Interactive Mode** | Claude prompts you through the process | Low |
| **Granola Integration** | Scan meetings for todos | Medium |
| **Enhanced Backlog** | Done section, auto-cleanup | Low |
| **Daily Wrap Up** | End-of-day reflections and learnings | Low |

---

## Calendar Integration

Connect to Google Calendar to:
- Create time blocks for your Top 3 priorities
- See today's meetings in your daily note
- Auto-schedule meeting prep time

### Setup (Google Calendar)

**Option 1: Claude Desktop with Google Calendar MCP**

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/notes"]
    },
    "google-calendar": {
      "command": "npx",
      "args": ["-y", "@anthropic-ai/mcp-server-google-calendar"]
    }
  }
}
```

You'll need to authenticate with Google on first use.

**Option 2: Manual calendar link**

In your daily template, add:

```markdown
## Today's Schedule

[Open Google Calendar](https://calendar.google.com)

| Time | Block | Task |
|------|-------|------|
| 9-11am | Deep Work | [Priority 1] |
| 2-3pm | Meeting Prep | [Prep for 3pm call] |
```

### Time Block Creation

After confirming Top 3 priorities, ask Claude:

```
Create calendar blocks for my Top 3:
1. "Finish proposal" - need 2 hours of deep work
2. "Client call prep" - need 30 min before 3pm meeting
3. "Review budget" - need 1 hour
```

Claude creates events with:
- Title: Task name
- Description: Link to today.md or context
- Color coding by priority (if supported)

### Meeting Import

Morning routine can include:

```
What meetings do I have today? Add them to my daily note.
```

Claude reads calendar and populates:

```markdown
## Meetings & Calls
| Time | Meeting | Prep Needed | Notes |
|------|---------|-------------|-------|
| 10:00 | Standup | None | |
| 14:00 | Client A Review | Review last week's metrics | |
| 16:00 | 1:1 with Manager | Prep talking points | |
```

---

## Time Blocking

Schedule focus time for priorities.

### In Morning Routine

After confirming Top 3, Claude asks:

```
Want to schedule time blocks for these?

1. "Finish proposal" - suggested: 9-11am (2hr deep work)
2. "Client call prep" - suggested: 1:30-2pm (before 2pm meeting)
3. "Review budget" - suggested: 4-5pm (end of day)

Create these blocks? (yes/adjust/skip)
```

### Block Format

```markdown
## Time Blocks

| Time | Focus | Task |
|------|-------|------|
| 9:00-11:00 | 🔴 Deep Work | Finish proposal |
| 13:30-14:00 | 🟡 Prep | Client call prep |
| 16:00-17:00 | 🟢 Admin | Review budget |
```

Color codes:
- 🔴 Deep Work - no interruptions
- 🟡 Prep - meeting preparation
- 🟢 Admin - flexible, interruptible

---

## Meeting Prep

Auto-generate prep notes before meetings.

### Trigger

When Claude sees a meeting in the next 2 hours:

```
You have "Client A Review" in 90 minutes. Generate prep notes?
```

### Prep Template

```markdown
## Meeting Prep: Client A Review (2pm)

**Attendees:** [from calendar]
**Last meeting:** [link to previous notes if found]

**Context:**
- [What's this about?]
- [Recent activity with this client]

**My goals:**
- [ ] [What I want to accomplish]

**Questions to ask:**
- [ ] [Question 1]

**Prep tasks:**
- [ ] Review last week's metrics
- [ ] Pull usage dashboard
```

### Auto-Detection

If using Granola, Claude can scan recent transcripts with this client for context.

---

## Weekly Planning (Monday Mode)

If it's Monday, start-my-day includes weekly planning.

### Trigger

Claude detects it's Monday and asks:

```
It's Monday. Want to do weekly planning before the daily routine?
```

### Weekly Planning Flow

1. **Review last week**
   ```
   Let me scan last week's daily notes...

   ## Last Week Summary
   - Completed: 23 tasks
   - Carried forward: 5 tasks
   - Pushed to backlog: 3 items
   - Recurring skips: "Exercise" (4 times)
   ```

2. **Check calendar**
   ```
   This week's key events:
   - Tuesday 2pm: Client A Review
   - Thursday: All-day offsite
   - Friday 10am: Board prep
   ```

3. **Set weekly priorities**
   ```
   Based on backlog and calendar, suggest weekly Top 3:
   1. Finish Q1 proposal (deadline Friday)
   2. Prep for Thursday offsite
   3. Board deck draft

   These work? Adjust?
   ```

4. **Then proceed to daily routine**

---

## Interactive Mode

Claude prompts you through the process instead of processing silently.

### Enable

```
Start my day in interactive mode
```

### Flow

Claude asks one question at a time:

```
Good morning! Let's get you set up.

1. How did you sleep? (good/ok/rough)
```

```
2. Any time constraints today? (meetings, hard stops, etc.)
```

```
3. What's top of mind right now? Just dump your thoughts:
```

```
4. Looking at yesterday's incomplete items:
   - "Send proposal" - carry forward or push to backlog?
   - "Review budget" - carry forward or push to backlog?
```

```
5. Based on everything, here are your suggested Top 3:
   1. Send proposal (carried, was urgent)
   2. Prep for 2pm client call
   3. [New from brain dump]

   Confirm or adjust?
```

### Benefits

- More thoughtful than rapid processing
- Good for heavy days when you need to think
- Catches nuance that bulk processing might miss

---

## Granola Integration (Meeting Todos)

For Granola users: scan transcripts for action items.

### Setup

1. Granola syncs to `Granola/` folder
2. Add to morning routine:

```
Scan Granola folder for new transcripts since yesterday.
Extract any action items assigned to me.
```

### Extraction

Claude reads new transcripts and finds:

```
## New from Meetings

### From "Client A Call" (yesterday 3pm)
- [ ] Send revised proposal by Friday - @me
- [ ] Schedule follow-up for next week - @me
- [x] Review their feedback - @client (waiting)

### From "Team Standup" (yesterday 9am)
- [ ] Update project tracker - @me
```

These get added to today.md tasks or backlog as appropriate.

---

## Enhanced Backlog

Better backlog management with Done section and auto-cleanup.

### Backlog Structure

```markdown
# Backlog

## To Review
- [ ] Item (pushed 2026-01-10)

## This Week
- [ ] Item (pulled 2026-01-14)

## Someday/Maybe
- [ ] Item

## Done (Last 7 Days)
- [x] Completed item (done 2026-01-14)
- [x] Another item (done 2026-01-12)

## Archived
- [x] Old item (archived 2026-01-05: no longer relevant)
```

### Done Section

When items complete:
1. Move to Done with completion date
2. Keep for 7 days (configurable)
3. Auto-archive after 7 days

### Cleanup Command

```
Clean up backlog
```

Claude:
1. Archives Done items older than 7 days
2. Flags To Review items older than 14 days
3. Reports what was cleaned

---

## Daily Wrap Up (End of Day)

Structured end-of-day reflection.

### Trigger

```
End my day
```

or

```
/end-of-day
```

### Flow

1. **Review today.md**
   ```
   Looking at today...

   Completed: 8 items
   Incomplete: 3 items
   - "Send proposal" (Must Do)
   - "Exercise" (Could Do)
   - "Call dentist" (Should Do)
   ```

2. **Disposition incomplete items**
   ```
   For each incomplete item:

   "Send proposal" (Must Do)
   → Carry to tomorrow / Push to backlog / Archive?
   ```

3. **Reflections**
   ```
   Quick reflection:

   What went well today?
   > [You answer]

   What got in the way?
   > [You answer]

   Any learnings to capture?
   > [You answer]
   ```

4. **Tomorrow's focus**
   ```
   Based on carried items and your reflection,
   tomorrow's Top 3 might be:

   1. Send proposal (carried, now 2 days stale)
   2. [From brain dump or backlog]
   3. [From brain dump or backlog]

   Note this for morning?
   ```

5. **Update files**
   - Complete reflection section in today.md
   - Move items to backlog with timestamps
   - Add learnings to a learnings log (optional)

### Learnings Log (Optional)

```markdown
# Learnings Log

## 2026-01-14
- Context switching killed my focus - need longer blocks
- Client A responds faster to Slack than email

## 2026-01-13
- Morning is best for deep work
```

---

## In-Progress Detection

If today.md already exists for today, don't recreate it.

### Detection

When `/start-my-day` runs:

1. Check if today.md exists
2. Check if date matches today
3. If yes: **In-Progress Mode**

### In-Progress Mode

```
Today.md already exists for today. Running update scan...

## Changes Since Last Check
- 2 new quick notes added
- 3 tasks completed
- Brain dump section has new content

## New Brain Dump Content
[Extract and process any new text in brain dump section]

## Suggested Updates
- Move completed tasks to Done
- Process new brain dump items
- Check for approaching meetings

Proceed with updates?
```

### What Gets Scanned

- New content in Brain Dump section
- Newly checked items (move to Done)
- Quick Notes section for actionable items
- Time (are any meetings coming up?)

---

## Implementation Priority

If building these out:

1. **Start with:** Interactive Mode, Enhanced Backlog, Daily Wrap Up
2. **Then add:** Weekly Planning, In-Progress Detection
3. **Finally:** Calendar Integration, Granola scanning, Meeting Prep

The first group is pure markdown/prompting. The second needs file comparison. The third needs external integrations.

---

*These are extensions. The core process works without any of them.*
