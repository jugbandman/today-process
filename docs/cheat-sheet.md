# Today Process Cheat Sheet

Print this. Keep it visible.

---

## Morning Routine (5-10 min)

```
1. BRAIN DUMP (2-3 min)
   └── Voice or type everything on your mind
   └── Don't organize, just dump

2. START MY DAY
   └── Claude Desktop: "Start my day. Here's my brain dump: [paste]"
   └── Claude Code: /start-my-day

3. REVIEW (2-3 min)
   └── Check Stale Items flagged by Claude
   └── Confirm Top 3 priorities
   └── Adjust task categories if needed
```

---

## Daily Commands

**Claude Desktop:**
```
Start my day. Read yesterday's note, check backlog, process this brain dump: [paste]
```

```
End my day. What didn't get done? Help me carry forward or push to backlog.
```

**Claude Code:**
```
/start-my-day
/end-of-day
/weekly-review
```

---

## Staleness Alerts

Claude flags items sitting too long:

| Alert | Meaning |
|-------|---------|
| ⚠️ Must Do 2+ days | This urgent thing keeps not happening |
| Should Do 3+ days | Consider demoting or just doing it |
| Waiting 7+ days | Time to follow up |
| Skipped 4+ times | Maybe archive this? |

**Don't ignore stale items.** Either do them, demote them, or push to backlog.

---

## Task Categories

| Category | What Goes Here |
|----------|----------------|
| **Must Do Today** | Hard deadlines, will break something if not done |
| **Should Do Today** | Important, but could slide to tomorrow |
| **Could Do If Time** | Nice to have, no pressure |
| **Waiting On Others** | Blocked - note who and since when |

---

## Backlog Flow

**Daily → Backlog:**
```
Push "Research CRM" to backlog
```
Claude adds with date: `- [ ] Research CRM (pushed 2026-01-14)`

**Backlog → Daily:**
```
Pull "Research CRM" forward to today
```

**Weekly Review:**
```
Weekly review - check stale backlog items
```

---

## End of Day (2 min)

Tell Claude:
```
End my day. Review what got done.
```

Claude will ask about incomplete items:
- **Carry forward** → moves to tomorrow's Must/Should
- **Push to backlog** → adds to _backlog.md with date
- **Archive** → removes (you decided not to do it)

---

## Weekly Review (10-15 min)

Run once per week (Sunday or Monday):

```
Weekly review
```

Claude checks:
- Backlog items sitting 7+ days
- Tasks you've skipped repeatedly
- Long-term Waiting On items

For each: Pull forward, keep, or archive.

---

## Quick Reference

| When | Do This |
|------|---------|
| Morning | Brain dump → Start my day → Confirm priorities |
| During day | Check off tasks, add notes |
| End of day | Review → Carry forward or push to backlog |
| Weekly | Review stale items, clean up backlog |

---

## If Things Break

| Problem | Fix |
|---------|-----|
| Stale items piling up | Do weekly review, be honest about archiving |
| Backlog growing forever | Weekly review, archive ruthlessly |
| Same task every day | Either schedule it as Must Do or admit you won't do it |
| Overwhelmed | Focus only on Must Do, ignore rest |

---

## Files

| File | Purpose |
|------|---------|
| `daily/today.md` | Today's command center |
| `daily/archive/` | Previous days |
| `_backlog.md` | Someday/maybe items |

---

*Full docs: [Setup Guide](setup-guide.md) | [README](../README.md)*
