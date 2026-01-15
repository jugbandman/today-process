# Backlog

Items not for today, but not forgotten.

---

## To Review

Items pushed from daily notes. Reviewed weekly.

<!-- Format: - [ ] Task description (pushed YYYY-MM-DD) -->


## This Week

Pulled forward for this week (not necessarily today).

<!-- Format: - [ ] Task (pulled YYYY-MM-DD) -->


## Someday/Maybe

No deadline, no urgency. Ideas and aspirations.

- [ ]

## Done (Last 7 Days)

Completed items. Auto-archived after 7 days during weekly review.

<!-- Format: - [x] Task (done YYYY-MM-DD) -->


## Archived

Decided not to do, or completed items older than 7 days.

<!-- Format: - [x] Task (archived YYYY-MM-DD: reason) -->


---

## How This Works

### Pushing from Daily
Tell Claude: "Push [task] to backlog"
It adds with timestamp: `- [ ] Task (pushed 2026-01-14)`

### Completing Backlog Items
Tell Claude: "Completed [task] from backlog"
It moves to Done: `- [x] Task (done 2026-01-14)`

### Weekly Review
Tell Claude: "Run weekly review"
- Archives Done items > 7 days
- Flags stale To Review items
- Reports patterns

### Staleness Alerts
| Section | Age | Alert |
|---------|-----|-------|
| To Review | 7+ days | "Review in weekly" |
| To Review | 14+ days | "2 weeks - archive?" |
| Done | 7+ days | Auto-archive |

---

*Last reviewed: YYYY-MM-DD*
