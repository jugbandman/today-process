---
name: start-my-day
description: Morning routine - archives yesterday, creates today.md, processes brain dump, flags stale items, suggests priorities. Handles in-progress files and Monday weekly planning. Invoke with /start-my-day.
---

# Start My Day

Morning workflow with in-progress detection, staleness tracking, and Monday planning.

## Paths (CUSTOMIZE THESE)

```
Vault:      /Users/YOUR_USERNAME/path/to/your/notes
Today:      daily/today.md
Archive:    daily/archive/YYYY/MM-month/
Template:   daily/templates/daily-template.md
Backlog:    _backlog.md
```

---

## Workflow

### Phase 0: Mode Detection

Check conditions:

1. **Is it Monday?** → Weekly Planning Mode first
2. **Does today.md exist for today?** → In-Progress Mode
3. **Otherwise** → Standard Mode

---

## Monday: Weekly Planning Mode

If Monday, run before standard routine:

```markdown
# Weekly Planning

It's Monday. Let's plan the week before diving into today.

## Last Week Review
[Scan last 5-7 daily notes from archive]

- Completed: [X] tasks
- Carried forward: [X] items
- Pushed to backlog: [X] items
- Recurring skips: [List items appearing 3+ times uncompleted]

## This Week's Calendar
[If calendar connected, list key events]
[Otherwise: "Check your calendar for key events this week"]

## Backlog Check
[Scan _backlog.md]

- Items in "This Week": [List]
- Stale in "To Review" (7+ days): [List]

## Weekly Top 3
Based on calendar and backlog, suggested weekly priorities:

1. [Suggested priority]
2. [Suggested priority]
3. [Suggested priority]

Confirm or adjust these weekly priorities?
```

After confirmation, proceed to standard routine.

---

## In-Progress Mode

If today.md exists with today's date, don't recreate - update instead.

### Detection

```
today.md found for [today's date].
Running update scan instead of full creation...
```

### Scan For

1. **New Brain Dump content**
   - Compare to previous read (if tracked)
   - Or check if Brain Dump section has content not yet processed
   - Extract new tasks

2. **Completed tasks**
   - Find `- [x]` items
   - Move to Done section or note for backlog

3. **New Quick Notes**
   - Scan for actionable items in notes
   - "Mentioned 'need to call Bob'" → suggest as task

4. **Time-based checks**
   - Any meetings in next 2 hours? → Meeting prep prompt
   - Is it afternoon? → Check progress on Top 3

### Output (In-Progress)

```markdown
## Update Scan Complete

**Since last check:**
- Brain dump: [New content found / No new content]
- Completed: 3 tasks since morning
- Quick notes: 2 new notes (1 actionable: "call Bob")

**Suggestions:**
- Add "Call Bob" to Should Do? (y/n)
- Move completed tasks to Done section? (y/n)

**Upcoming:**
- Meeting "Client Review" in 90 minutes
  → Generate prep notes? (y/n)
```

---

## Standard Mode

Full morning routine when starting fresh.

### Phase 1: Health Check

```bash
ls "$VAULT_PATH" > /dev/null && echo "Vault: OK"
```

Check:
- Vault accessible
- Today.md status (exists? what date?)
- Days since last archive

### Phase 2: Staleness Check

Read recent archived notes. Flag:

| Location | Age | Alert |
|----------|-----|-------|
| Must Do | 2+ days | "⚠️ [task] - Must Do for [N] days" |
| Should Do | 3+ days | "[task] - Should Do for [N] days" |
| Waiting On | 7+ days | "[task] - waiting [N] days" |
| Recurring | 4+ times | "[task] - skipped [N] times" |

### Phase 3: Archive Yesterday

If today.md exists with old date:

1. Rename to `YYYY-MM-DD.md`
2. Move to `archive/YYYY/MM-month/`
3. Record incomplete items for carry forward

### Phase 4: Create Today.md

1. Copy from template
2. Set date, previous note link
3. Add Stale Items section (from Phase 2)
4. Carry forward incomplete tasks
   - Add: `(carried from [date])`
5. Check backlog "This Week" for suggestions

### Phase 5: Process Brain Dump

If brain dump provided:

1. **Extract actions** - Verbs: need, should, must, send, call, finish, etc.
2. **Identify context** - People, deadlines, urgency
3. **Categorize** - Must/Should/Could/Waiting
4. **Deduplicate** - Check against carried items and backlog
5. **Update tasks section**

### Phase 6: Suggest Priorities

Based on:
1. Stale items (they've been waiting)
2. Deadline items
3. Carried forward items
4. New urgent items from brain dump

```
Suggested Top 3:
1. "Send proposal" - 3 days stale, make it happen
2. "Client call prep" - meeting at 2pm
3. "Review budget" - carried from yesterday

Confirm or adjust?
```

### Phase 7: Time Blocking (Optional)

If calendar connected, offer:

```
Want to block time for your Top 3?

1. "Send proposal" → 9-11am (2hr deep work)?
2. "Client call prep" → 1:30pm (30min before meeting)?
3. "Review budget" → 4-5pm (1hr)?

Create these blocks? (yes/adjust/skip)
```

---

## Interactive Mode

For prompted walkthrough:

```
/start-my-day interactive
```

Asks questions one at a time:
1. How are you feeling today?
2. Any hard constraints (meetings, deadlines)?
3. Brain dump?
4. Disposition of each carried item
5. Confirm priorities

---

## Output (Standard)

```markdown
# Good morning!

## Status
- [x] Yesterday archived
- [x] Today.md created for [date]
- [x] Carried forward: [N] items
- [x] Brain dump processed: [N] tasks

## ⚠️ Stale Items
- "Send proposal" - Must Do for 3 days
- "Follow up with Bob" - Should Do for 4 days

## Suggested Top 3
1. [Priority with reasoning]
2. [Priority with reasoning]
3. [Priority with reasoning]

Confirm priorities? (yes/adjust)
```

---

## Modes Summary

| Mode | Trigger | What Happens |
|------|---------|--------------|
| **Standard** | No today.md for today | Full creation routine |
| **In-Progress** | Today.md exists for today | Update scan only |
| **Monday** | It's Monday | Weekly planning first, then standard |
| **Interactive** | `/start-my-day interactive` | Prompted walkthrough |
| **Quick** | `/start-my-day quick` | Minimal prompts, fast processing |

---

## Autonomy Rules

**Do automatically:**
- Archive yesterday
- Create/update today.md
- Extract tasks from brain dump
- Carry forward incomplete items
- Flag stale items

**Ask first:**
- Priority order confirmation
- Weekly planning confirmation (Monday)
- Time block creation
- Moving items to backlog
