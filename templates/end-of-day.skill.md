---
name: end-of-day
description: Daily wrap up - review completed work, disposition incomplete items, capture reflections and learnings, prep for tomorrow. Invoke with /end-of-day.
---

# End of Day

Structured end-of-day wrap up: review, reflect, learn, prep tomorrow.

## Paths (CUSTOMIZE THESE)

```
Vault:      /Users/YOUR_USERNAME/path/to/your/notes
Today:      daily/today.md
Backlog:    _backlog.md
Learnings:  _learnings.md (optional)
```

---

## Workflow

### Phase 1: Review Today

Read today.md and summarize:

```markdown
## Today's Summary

**Completed:** 8 items
- [List completed tasks]

**Incomplete:** 3 items
- "Send proposal" (Must Do) - 2 days stale
- "Exercise" (Could Do)
- "Call dentist" (Should Do)

**Meetings attended:** 2
**Notes captured:** 5 quick notes
```

### Phase 2: Disposition Incomplete Items

For each incomplete item, ask:

```
"Send proposal" (Must Do, 2 days stale)
Options:
1. Carry forward to tomorrow (stays Must Do)
2. Push to backlog (with today's date)
3. Archive (decided not to do)

Which? [1/2/3]
```

**If carrying forward:**
- Note in reflection: "Carrying: Send proposal (now 2 days)"
- Will appear in tomorrow's Stale Items

**If pushing to backlog:**
- Add to `_backlog.md` To Review section
- Format: `- [ ] Send proposal (pushed YYYY-MM-DD)`

**If archiving:**
- Add to `_backlog.md` Archived section
- Format: `- [x] Send proposal (archived YYYY-MM-DD: [reason])`
- Ask for brief reason

### Phase 3: Capture Reflections

Prompt for reflections:

```
Quick reflection time.

**What went well today?**
> [User input - or "skip"]

**What got in the way?**
> [User input - or "skip"]

**Energy/focus level?** (1-5)
> [User input - or "skip"]
```

Update today.md End of Day Reflection section.

### Phase 4: Capture Learnings

```
Any learnings worth noting?
(Things you'd want to remember, patterns you noticed, insights)

> [User input - or "skip"]
```

If learnings provided:
- Add to today.md Quick Notes
- Optionally append to `_learnings.md` with date

### Phase 5: Tomorrow's Focus

Based on:
- Carried forward items
- Stale items (prioritize these)
- Backlog "This Week" items
- Any mentioned in reflection

Suggest:

```
Based on today, tomorrow's Top 3 might be:

1. Send proposal (carried, 2 days stale - make it happen)
2. Prep for Thursday meeting (from calendar)
3. [From backlog This Week]

Note these for tomorrow morning? (yes/adjust/skip)
```

If yes, add to today.md or create a `tomorrow-focus.md` temp file.

### Phase 6: Final Updates

1. **Update today.md**
   - Fill in End of Day Reflection
   - Mark disposition of items
   - Add any learnings to Quick Notes

2. **Update backlog**
   - Add pushed items with timestamps
   - Add archived items with reasons
   - Move any completed backlog items to Done

3. **Git commit** (if using git)
   ```bash
   git add -A && git commit -m "End of day: [date]"
   ```

---

## Output

Final summary:

```markdown
## Day Complete

**Completed:** 8 tasks
**Carried forward:** 2 items (will be flagged stale)
**Pushed to backlog:** 1 item
**Archived:** 0 items

**Tomorrow's suggested focus:**
1. Send proposal (2 days stale)
2. Prep for Thursday meeting
3. Review budget

**Reflection captured:** Yes
**Learnings noted:** 1 item

Files updated:
- daily/today.md (reflection added)
- _backlog.md (1 item pushed)

Have a good evening! 🌙
```

---

## Interactive Mode

Default is interactive (asks questions). For quick mode:

```
/end-of-day quick
```

Quick mode:
- Carries all incomplete to tomorrow
- Skips reflection prompts
- Just summarizes and updates files

---

## Autonomy Rules

**Do automatically:**
- Read and summarize today.md
- Calculate what's complete/incomplete
- Update files after decisions

**Ask first:**
- Disposition of each incomplete item
- Reflection prompts
- Tomorrow's focus confirmation

---

## Tips

- Do this at a consistent time (e.g., 5pm)
- Even 2 minutes of reflection helps
- Be honest about archiving things you won't do
- Patterns in reflections → insights over time
