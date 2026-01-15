---
name: start-my-day
description: Morning routine - archives yesterday, creates today.md, processes brain dump, flags stale items, suggests priorities. Invoke with /start-my-day.
---

# Start My Day

Morning workflow: archive yesterday, check staleness, create today.md, process brain dump, suggest priorities.

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

### Phase 1: Health Check

```bash
# Verify access
ls "$VAULT_PATH" > /dev/null && echo "Vault: OK"
```

Check what exists:
- Does today.md exist? What date?
- How many days since last archive?
- Any items in backlog?

### Phase 2: Staleness Check

**Read yesterday's note** (or last archived note). Look for:

1. **Stale Must Do items**
   - Any `- [ ]` in Must Do section that was also there 2+ days ago
   - Flag with days: "Send proposal (3 days in Must Do)"

2. **Stale Should Do items**
   - Any `- [ ]` in Should Do for 3+ days
   - Flag: "Review budget (4 days in Should Do)"

3. **Recurring patterns**
   - Same task text appearing multiple days unchecked
   - "Exercise has appeared 5 times, never completed"

4. **Stale Waiting On**
   - Items waiting 7+ days
   - "Waiting on Bob since Jan 5 (10 days)"

**Output stale items to include in today.md Stale Items section.**

### Phase 3: Archive Yesterday

If today.md exists with old date:

1. Rename to `YYYY-MM-DD.md`
2. Move to `archive/YYYY/MM-month/`
3. Note what was incomplete (for carry forward)

### Phase 4: Create Today.md

1. Copy from template
2. Fill in date
3. Add previous note link
4. **Add Stale Items section** with flagged items
5. Carry forward incomplete `- [ ]` tasks from yesterday
   - Add note: `(carried from [date])`

### Phase 5: Check Backlog

Read `_backlog.md`. Look for:

1. Items in "This Week" section → suggest for today
2. Items marked urgent or with approaching deadlines
3. Anything pushed 7+ days ago (flag for weekly review)

### Phase 6: Process Brain Dump

If user provides brain dump:

1. **Extract action items** - Look for verbs:
   - "need to", "should", "have to", "must"
   - "send", "call", "email", "follow up"
   - "finish", "complete", "submit", "review"

2. **Identify context**
   - People mentioned → link or note
   - Deadlines mentioned → flag for Must Do
   - Urgency language → categorize appropriately

3. **Categorize tasks:**
   - Explicit deadlines today → Must Do Today
   - Urgent language + no deadline → Must Do Today
   - Important, flexible timing → Should Do Today
   - Nice to have → Could Do If Time
   - Waiting on someone → Waiting On Others

4. **Check for duplicates**
   - Is this task already in today.md (carried forward)?
   - Is it in backlog?
   - Merge rather than duplicate

5. **Update Tasks section** with extracted items

### Phase 7: Suggest Priorities

Based on:
- Stale items (highest priority - they've been waiting)
- Deadline items
- Carried forward items
- New urgent items from brain dump

Suggest Top 3, explain reasoning:

```
Suggested Top 3:
1. "Send proposal to Client A" - been in Must Do 3 days, deadline today
2. "Follow up with Bob" - marked urgent in brain dump
3. "Prep for Thursday meeting" - carried forward from yesterday

These OK, or want to adjust?
```

---

## Staleness Tracking

| Location | Age | Alert |
|----------|-----|-------|
| Must Do | 2+ days | "⚠️ [task] - Must Do for [N] days" |
| Should Do | 3+ days | "[task] - Should Do for [N] days, demote?" |
| Waiting On | 7+ days | "[task] - waiting [N] days, follow up?" |
| Backlog To Review | 7+ days | Flag for weekly review |
| Recurring skip | 4+ times | "[task] - skipped [N] times, archive?" |

### How to Detect Staleness

**Option 1: Date parsing**
If items include dates: `(carried from 2026-01-10)`, calculate from that.

**Option 2: Archive comparison**
Read last 3-5 archived daily notes. If same task text appears:
- Unchecked in 2+ consecutive Must Do → stale
- Unchecked in 3+ consecutive Should Do → stale
- Appearing 4+ times total → recurring skip

**Option 3: Backlog timestamps**
Items in backlog have `(pushed YYYY-MM-DD)` - calculate from that.

---

## Autonomy Rules

**Do automatically:**
- Archive yesterday's note
- Create new today.md
- Extract and categorize tasks from brain dump
- Carry forward incomplete items
- Identify and flag stale items

**Ask first:**
- Final priority order
- Moving items to backlog
- Archiving or deleting anything
- Ambiguous categorization

---

## Output

After running, report:

```markdown
# Good morning!

## Status
- [x] Yesterday archived to daily/archive/2026/01-january/2026-01-13.md
- [x] Today.md created for Tuesday, January 14
- [x] Carried forward: 3 incomplete items
- [x] Brain dump processed: 5 tasks extracted

## ⚠️ Stale Items
- "Send proposal to Client A" - Must Do for 3 days
- "Follow up with Bob" - Should Do for 4 days

## Suggested Top 3
1. Send proposal to Client A (3 days stale, deadline today)
2. [New from brain dump]
3. [Carried from yesterday]

Confirm priorities, or tell me what to adjust.
```

---

## Notes

- Staleness flags are reminders, not judgments
- Some items legitimately stay in Should Do for days
- The goal is awareness, not guilt
- Weekly review handles deeper cleanup
