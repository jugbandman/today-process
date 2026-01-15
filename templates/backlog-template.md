# Backlog

Items not for today, but not forgotten.

---

## To Review

Items pushed from daily notes. Reviewed weekly.

<!-- Format: - [ ] Task description (pushed YYYY-MM-DD) -->


## This Week

Pulled forward from backlog for this week (not necessarily today).

<!-- Format: - [ ] Task (pulled YYYY-MM-DD) -->
- [ ]

## Someday/Maybe

No deadline, no urgency. Ideas and aspirations.

- [ ]

## Waiting On (Long-term)

Blocked items with no immediate resolution expected.

<!-- Format: - [ ] Task - waiting on [person/thing] since YYYY-MM-DD -->


---

## Done (Last 7 Days)

Completed items. Auto-archived after 7 days.

<!-- Format: - [x] Task (done YYYY-MM-DD) -->


## Archived

Decided not to do, or completed items older than 7 days.

<!-- Format: - [x] Task (archived YYYY-MM-DD: reason) -->


---

## How This Works

### Daily → Backlog

When you don't finish something and it's not urgent:

```
Push "Research CRM options" to backlog
```

Claude adds with timestamp:
```markdown
- [ ] Research CRM options (pushed 2026-01-14)
```

### Completing Backlog Items

When you finish something from backlog:

```
Completed "Research CRM" from backlog
```

Claude moves to Done:
```markdown
## Done (Last 7 Days)
- [x] Research CRM options (done 2026-01-14)
```

### Weekly Cleanup

During weekly review, Claude:

1. **Archives Done items older than 7 days**
   - Moves from Done to Archived
   - Adds: `(archived YYYY-MM-DD: completed)`

2. **Flags stale To Review items**
   - 7+ days: "Consider addressing or archiving"
   - 14+ days: "This has been sitting 2 weeks"

3. **Reports patterns**
   - "You've pushed 'Exercise' 3 times without doing it"

### Manual Cleanup

```
Clean up backlog
```

Claude:
- Archives Done items > 7 days
- Flags stale items
- Reports what was cleaned

---

## Staleness Alerts

| Section | Age | Alert |
|---------|-----|-------|
| To Review | 7+ days | "Review in weekly" |
| To Review | 14+ days | "2 weeks - archive?" |
| This Week | Not done by Sunday | "Didn't happen - push back?" |
| Waiting On | 14+ days | "Follow up or archive?" |
| Done | 7+ days | Auto-archive |

---

## Section Guide

| Section | What Goes Here |
|---------|----------------|
| **To Review** | Pushed from daily, needs weekly review |
| **This Week** | Committed to doing this week |
| **Someday/Maybe** | No timeline, just ideas |
| **Waiting On** | Blocked, long-term wait |
| **Done** | Recently completed (7 day holding) |
| **Archived** | Decided not to do, or old completed |

---

*Last reviewed: YYYY-MM-DD*
*Last cleanup: YYYY-MM-DD*
