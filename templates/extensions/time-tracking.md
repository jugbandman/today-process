# Time Tracking Extension

> Optional extension for billing clients by the hour.

## When to Use

Add this extension if you:
- Bill clients hourly
- Need to track time for invoicing
- Want weekly time summaries

## Setup

### 1. Create Client Time Logs

For each paying client, create `projects/client-name/_timelog.md`:

```markdown
# Client Name Time Log

> Time tracking for invoicing.

## January 2026

| Date | Hours | Description |
|------|-------|-------------|
| 2026-01-14 | 2.0 | Research, meeting prep |
| 2026-01-15 | 1.5 | Client call, follow-up |

## December 2025

| Date | Hours | Description |
|------|-------|-------------|
|      |       |             |
```

### 2. Enable in Skills

The time tracking phases are marked "(Optional Extension)" in each skill:

- **End-of-day Phase 3** - Prompts for time after disposition
- **Start-my-day Phase 2** - Catches yesterday's missed entries
- **Weekly review Phase 3** - Audits entire week for gaps

## How It Works

### Daily (End-of-Day)

```
I noticed work on paying clients today:

**Client A**
- "Research task" - completed
- "Meeting prep" - completed

Estimated time? (e.g., "2h", "1.5h", or "skip")
```

### Morning Catch-Up

If end-of-day was skipped:

```
⚠️ Missing Time Entry

Yesterday's note shows client work but no time logged:

**Client A**
- "Research task" - completed

Estimated time for yesterday? (e.g., "2h", "skip")
```

### Weekly Audit

```
## Week's Time Summary

**Client A:** 6.5h (Mon 2h, Tue 1.5h, Thu 3h)
**Client B:** 2.0h (Wed 2h)

Ready for spreadsheet export.
```

## Invoicing Workflow

1. Open client's `_timelog.md`
2. Copy the relevant month's table
3. Paste into Google Sheets or Excel
4. Format as needed

The table format is designed for direct copy/paste.

## Cascading Safety Net

| Checkpoint | What It Catches |
|------------|-----------------|
| End-of-day | Today's time |
| Start-my-day | Yesterday's missed time |
| Weekly review | Any gaps in the week |

Miss one checkpoint? The next one catches it.
