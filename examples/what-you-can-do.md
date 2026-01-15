# What You Can Do with Today Process

Real examples of AI-powered daily workflow in action.

---

## Morning Scenarios

### Basic: Process a Brain Dump

**You say:**
```
/start-my-day

Brain dump: Need to send that proposal to Sarah, forgot about the dentist
appointment, client meeting at 2pm should prepare for that, been putting off
the expense report for days, waiting to hear back from Mike about the budget
```

**AI does:**
```markdown
## Brain Dump Processed

Extracted 5 items:

### Must Do Today
- [ ] Send proposal to Sarah
- [ ] Prepare for 2pm client meeting

### Should Do Today
- [ ] Complete expense report (you mentioned putting it off)

### Could Do If Time
- [ ] Dentist appointment (noted - add to calendar?)

### Waiting On Others
- [ ] Mike - budget feedback

Suggested Top 3:
1. Send proposal to Sarah (action item, specific person)
2. Prepare for client meeting (time-bound, 2pm)
3. Expense report (you mentioned procrastinating)

Confirm? (y/adjust)
```

---

### Intermediate: Staleness Detection

**Scenario:** You've had "Send proposal to Sarah" in Must Do for 3 days.

**AI says (at start of day):**
```markdown
## ⚠️ Stale Items Detected

- "Send proposal to Sarah" - in Must Do for **3 days**
  → This keeps getting carried forward. What's blocking it?

- "Review Q4 metrics" - in Should Do for **4 days**
  → Should this be promoted to Must Do or pushed to backlog?

For "Send proposal to Sarah":
1. Keep in Must Do (make it happen today)
2. Push to backlog (not actually urgent)
3. Add context (what's blocking?)
```

---

### Advanced: Monday Planning

**Scenario:** It's Monday morning.

**AI automatically adds:**
```markdown
# Weekly Planning

It's Monday. Let's plan the week before diving into today.

## Last Week Review
- Completed: 12 tasks
- Carried forward: 3 items
- Pushed to backlog: 2 items
- Recurring skips: "Exercise" (appeared 4 times, done 0)

## This Week's Backlog Items
- "Research CRM options" - pushed 8 days ago (stale)
- "Update documentation" - in This Week section

## Suggested Weekly Priorities
1. Clear the stale "Research CRM" - it's been waiting
2. Client deliverable due Thursday
3. Address the "Exercise" pattern (schedule or archive?)

Confirm weekly focus? (y/adjust)
```

---

## Mid-Day Scenarios

### Re-running During the Day (In-Progress Mode)

**You say:** `/start-my-day` (when today.md already exists)

**AI does:**
```markdown
## Update Scan

today.md found for January 14, 2026.
Running update scan (not recreating file)...

**Since this morning:**
- Completed: 2 tasks (✓ Send proposal, ✓ Client meeting prep)
- New brain dump content: None detected
- New quick notes: 1 actionable ("call Bob back")

**Suggestions:**
- Add "Call Bob back" to Should Do? (y/n)
- Meeting "Team Standup" in 45 minutes - need prep? (y/n)

**Progress on Top 3:**
1. ✓ Send proposal to Sarah - DONE
2. ✓ Client meeting prep - DONE
3. ⏳ Expense report - not started

You're 2/3 on your Top 3. Nice work!
```

---

### Adding a Brain Dump Mid-Day

**You say:**
```
Just finished the client meeting. Brain dump:

They want the revised proposal by Friday, need to loop in the design team,
Sarah mentioned budget concerns we should address, follow up with Mike
about the timeline
```

**AI does:**
```markdown
## Mid-Day Brain Dump Processed

New items extracted:

### Must Do Today
- [ ] Loop in design team on revised proposal

### Should Do Today
- [ ] Address budget concerns in proposal (Sarah's feedback)

### Waiting On Others
- [ ] Mike - timeline confirmation (added to existing wait)

### This Week (not today)
- [ ] Revised proposal due Friday

Updated your task list. Want me to re-suggest Top 3 for the afternoon?
```

---

## End of Day Scenarios

### Basic End of Day

**You say:** `/end-of-day`

**AI does:**
```markdown
## Today's Summary

**Completed:** 4 items
- ✓ Send proposal to Sarah
- ✓ Client meeting prep
- ✓ Loop in design team
- ✓ Call Bob back

**Incomplete:** 2 items
- "Expense report" (Should Do) - carried 1 day
- "Review Q4 metrics" (Could Do) - carried 4 days

---

## Disposition

For each incomplete item:

**"Expense report"** (Should Do, 1 day)
→ 1. Carry to tomorrow (stays Should Do)
→ 2. Promote to Must Do
→ 3. Push to backlog

**"Review Q4 metrics"** (Could Do, 4 days)
→ 1. Carry to tomorrow
→ 2. Push to backlog
→ 3. Archive (not doing)
```

---

### With Reflections

**AI prompts:**
```markdown
## Quick Reflection

**What went well today?**
> (type response or "skip")

**What got in the way?**
> (type response or "skip")

**Any learnings worth noting?**
> (type response or "skip")
```

**You say:** "Got the proposal done finally. Got distracted by Slack too much. skip"

**AI does:**
```markdown
## Reflection Captured

**What went well:** Got the proposal done finally
**What blocked:** Got distracted by Slack too much
**Learnings:** (skipped)

---

## Tomorrow's Suggested Focus

Based on today:
1. Expense report (carried, address early before distractions)
2. Revised proposal edits (due Friday, start tomorrow)
3. Review Q4 metrics (or push to backlog - it's been 4 days)

Note these for tomorrow? (y/adjust)
```

---

## Weekly Review Scenarios

### Standard Weekly Review

**You say:** `/weekly-review`

**AI does:**
```markdown
## Weekly Review

### Done Items (archiving)
Moving 8 completed items older than 7 days to Archived section.

### Stale in Backlog

**To Review (7+ days):**
- "Research CRM options" - pushed 12 days ago
- "Update resume" - pushed 9 days ago

**To Review (14+ days):**
- "Learn Spanish" - pushed 21 days ago

### Recurring Patterns

- "Exercise" appeared in daily notes 4 times, completed 0 times
- "Read industry news" appeared 3 times, completed 1 time

---

## Decisions Needed

**"Research CRM options"** (12 days in To Review)
→ 1. Pull to This Week (commit to doing)
→ 2. Archive (not doing)
→ 3. Keep in To Review

**"Exercise"** (skipped 4 times)
→ 1. Schedule as Must Do (force it)
→ 2. Archive (accept you won't)
→ 3. Different approach (morning only?)
```

---

## Adaptive Workflow Examples

### First Time Setup

**AI detects no config file:**
```markdown
## Welcome to Today Process!

I'll ask a few questions to customize your workflow.

**Question 1/4:** Where are your notes stored?
> Current directory: /Users/you/Documents/Notes
> Is this correct? (y/n/different path)
```

### Pattern Recognition

**After 2 weeks of use:**
```markdown
## Workflow Suggestion

I noticed a pattern:
- You add items to "Waiting On" but rarely check them
- 3 items have been waiting 14+ days without follow-up

**Suggestion:** Want me to prompt you to review "Waiting On"
items every Friday as part of end-of-day?

> (y/n/stop asking suggestions)
```

### User Says "Stop Asking"

**You say:** "stop asking setup questions"

**AI responds:**
```markdown
Got it! I won't ask configuration questions anymore.

You can always run `/configure-workflow` to adjust settings manually.

Current configuration saved to: daily/.today-process-config.md
```

---

## Power User Scenarios

### Quick Mode (Minimal Prompts)

**You say:** `/start-my-day quick`

**AI does:**
```markdown
## Quick Start

- Yesterday archived ✓
- Today.md created ✓
- 2 items carried forward
- No stale items (under threshold)

Ready to go. Add brain dump when ready.
```

### Interactive Mode (Guided)

**You say:** `/start-my-day interactive`

**AI does:**
```markdown
## Interactive Morning

**Step 1/5:** How are you feeling today?
> (energized / normal / tired / stressed)

**Step 2/5:** Any hard constraints today?
> (meetings, deadlines, appointments)

**Step 3/5:** Brain dump time. What's on your mind?
> (speak or type freely)

[continues through each step with confirmation]
```

---

## Integration Examples

### With Granola (Meeting Transcripts)

**AI detects new transcript:**
```markdown
## New Meeting Transcript

Found: "Client Review - 2026-01-14.md" in Granola/

**Extracted action items:**
- [ ] Send revised proposal by Friday (assigned: you)
- [ ] Schedule follow-up meeting (assigned: you)
- [ ] Review budget numbers (assigned: Sarah)

**Add your items to today's tasks?** (y/n)
**Create follow-up with Sarah?** (y/n)
```

### With Calendar (Time Blocking)

**AI offers:**
```markdown
## Time Blocking

Your Top 3 today:
1. Expense report (estimate: 1 hour)
2. Revised proposal edits (estimate: 2 hours)
3. Team planning doc (estimate: 1 hour)

Your calendar shows:
- 10am-11am: Free
- 11am-12pm: Standup
- 12pm-2pm: Free
- 2pm-3pm: Client call
- 3pm-5pm: Free

**Suggested blocks:**
1. 10-11am: Expense report
2. 12-2pm: Revised proposal edits
3. 3-4pm: Team planning doc

Create these calendar blocks? (y/adjust/skip)
```

---

*These examples show what's possible. Your actual workflow will be customized to your preferences through the adaptive onboarding system.*
