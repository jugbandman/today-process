---
name: weekly-review
description: Weekly backlog review - surfaces stale items, recurring skips, and helps clean up. Run on Sunday/Monday or whenever you plan your week. Invoke with /weekly-review.
---

# Weekly Review

Review backlog, surface stale items, clean up recurring skips, plan the week.

## Paths (CUSTOMIZE THESE)

```
Vault:      /Users/YOUR_USERNAME/path/to/your/notes
Backlog:    _backlog.md
Daily:      daily/today.md
Archive:    daily/archive/
```

---

## Workflow

### Phase 1: Scan Backlog

Read `_backlog.md` and identify:

1. **Stale items** - In "To Review" for 7+ days
   - Parse `(pushed YYYY-MM-DD)` to calculate age
   - Flag anything over 7 days

2. **Long-sitting items** - In "Someday/Maybe" for 30+ days
   - These may need archiving or a decision

3. **Stuck waiting** - In "Waiting On" for 14+ days
   - May need a follow-up or escalation

### Phase 2: Scan Recent Daily Notes

Read last 5-7 daily notes from archive. Look for:

1. **Recurring incomplete tasks**
   - Same task text appearing 3+ times unchecked
   - "You've had 'Exercise' in Could Do 5 times - never done"

2. **Carried forward repeatedly**
   - Tasks that keep moving day to day
   - Suggests it's either not important or blocked

3. **Patterns**
   - What categories get done vs skipped
   - Time of week patterns

### Phase 3: Time Tracking Audit (Optional Extension)

If time tracking is enabled, check for missing entries this week:

1. **Scan last 7 daily notes** - Find completed client work
2. **Check client timelogs** - Verify entries exist for each day

**If gaps found:**

```markdown
## ⚠️ Missing Time Entries

**Monday 2026-01-13**
- Client A: "Research task" (no time logged)

**Wednesday 2026-01-15**
- Client B: "Meeting prep" (no time logged)

Fill in missing time? (enter estimates or "skip")
```

**Weekly summary:**
```markdown
## Week's Time Summary

**Client A:** 6.5h (Mon 2h, Tue 1.5h, Thu 3h)
**Client B:** 2.0h (Wed 2h)

Ready for spreadsheet export.
```

### Phase 4: Present Findings

Output format:

```markdown
# Weekly Review: [Date Range]

## Stale in Backlog (7+ days)

| Item | Days | Recommendation |
|------|------|----------------|
| Research CRM options | 9 | Pull forward or archive? |
| Redesign onboarding | 14 | Been 2 weeks - still relevant? |

## Recurring Incomplete

| Item | Occurrences | Last 7 Days |
|------|-------------|-------------|
| Exercise | 5 times | Never completed |
| Read industry news | 4 times | Completed once |

## Long-term Waiting

| Item | Waiting On | Since | Suggestion |
|------|------------|-------|------------|
| Budget approval | Finance team | 12 days | Follow up? |

## Questions for You

1. "Research CRM options" (9 days) - Pull to this week, or archive?
2. "Exercise" keeps appearing but never gets done - Schedule it as Must Do, or remove?
3. "Budget approval" stuck for 12 days - Time to escalate?

---

What would you like to do with these items?
```

### Phase 5: Process Decisions

Based on user response:

**Pull forward:**
- Move item from backlog "To Review" to "This Week"
- Update date: `(pulled YYYY-MM-DD)`

**Keep in backlog:**
- Leave item, update timestamp to today
- `(reviewed YYYY-MM-DD, keeping)`

**Archive:**
- Move to "Archived" section
- Add reason: `(archived YYYY-MM-DD: reason)`

**Delete:**
- Remove from backlog entirely
- (Only if user explicitly confirms)

### Phase 6: Plan the Week

After cleanup, ask:

```
Backlog is cleaned up. Looking at what's left:

## Available for This Week
[List items in "This Week" section]

## Open from Backlog
[List items still in "To Review"]

What are your 3-5 priorities for this week?
```

Update "This Week" section with confirmed priorities.

---

## Autonomy Rules

**Do automatically:**
- Read and analyze backlog
- Read recent daily notes
- Calculate staleness
- Present findings

**Ask first:**
- Moving items between sections
- Archiving anything
- Deleting anything

---

## Staleness Thresholds

| Location | Threshold | Action |
|----------|-----------|--------|
| To Review | 7 days | Flag for decision |
| To Review | 14 days | Strongly suggest archive |
| Someday/Maybe | 30 days | Ask if still relevant |
| Waiting On | 14 days | Suggest follow-up |
| Same task 3+ times | N/A | Ask about pattern |

---

## Output

After completing review:

```markdown
## Weekly Review Complete

**Reviewed:** [count] backlog items, [count] daily notes
**Pulled forward:** [count] items
**Archived:** [count] items
**This week's priorities:** [list]

Next review: [date + 7 days]
```

---

## Notes

- Run weekly, ideally same day/time
- Sunday evening or Monday morning work well
- Takes 10-15 minutes
- Prevents backlog from becoming a graveyard
