# Implementation Example

How one person (a consultant with multiple clients) set up the Today Process.

---

## Context

- **Role:** Independent consultant, fractional CRO work
- **Challenge:** Multiple clients, job search, family obligations - lots of context switching
- **Tools:** Obsidian, Claude Code, Granola for meetings, Git for sync

---

## Folder Structure

```
vault/
├── ++Home/                    # Navigation MOCs
├── 00-inbox/                  # Quick capture
├── 01-daily/                  # Today Process lives here
│   ├── today.md
│   ├── templates/
│   │   └── daily-template.md
│   ├── archive/
│   │   └── 2026/
│   │       └── 01-january/
│   └── _backlog.md            # Someday/maybe items
├── 02-business/               # Consulting practice
├── 03-projects/               # Client work + personal projects
├── 04-people/                 # Contact notes
├── 05-organizations/          # Company notes
├── Granola/                   # Meeting transcripts (auto-synced)
└── CLAUDE.md                  # AI configuration
```

**Why this structure:**
- Numbers keep folders sorted
- Projects separated from business operations
- People and orgs as first-class entities (easy to link)
- Granola folder for auto-synced meeting notes

---

## Daily Note Customizations

Added beyond the basic template:

### Client Sections

```markdown
## Active Commitments

### [[03-projects/client-a/_MOC|Client A]] (Contact Name)
- [ ] Specific deliverable
- [ ] Meeting prep for Friday

### [[03-projects/client-b/_MOC|Client B]] (Contact Name)
- [ ] Another commitment
```

**Why:** Surfaces what's owed to each client at a glance.

### Job Search Pipeline

```markdown
## Job Search

| Opportunity | Status | Next Step |
|-------------|--------|-----------|
| Company A | Interview scheduled | Prep for Thursday |
| Company B | Waiting on feedback | Follow up Monday |
```

**Why:** Active job search alongside consulting - needs daily visibility.

### Personal/Family Section

```markdown
## Personal
- [ ] Kids pickup 3pm
- [ ] Dentist Thursday
- [ ] Anniversary dinner planning
```

**Why:** Life doesn't stop for work. Keeping it visible prevents conflicts.

### Transcript Storage

```markdown
## Transcripts

<details>
<summary>Morning brain dump (click to expand)</summary>

[Raw transcript preserved for reference]

</details>
```

**Why:** Sometimes want to check what was actually said vs extracted.

---

## Commitment Surfacing

The `/start-my-day` skill scans these locations for open items:

| Source | What It Finds |
|--------|---------------|
| `03-projects/*/_MOC.md` | Project-level commitments |
| `02-business/_MOC.md` | Business priorities |
| `04-people/*.md` | What's owed to specific people |

The skill looks for:
- `- [ ]` unchecked items
- "I owe" or "need to send" phrases
- Items with names/dates attached

---

## Meeting Integration

Using Granola + Obsidian Granola Sync plugin:

1. Granola records all meetings automatically
2. Transcripts sync to `Granola/` folder
3. `/start-my-day` processes new transcripts:
   - Adds frontmatter (date, attendees)
   - Extracts action items
   - Links to people entities

**Example processed transcript:**

```markdown
---
type: meeting
date: 2026-01-14
attendees: [[04-people/sarah-jones|Sarah Jones]], [[04-people/bob-smith|Bob Smith]]
company: [[05-organizations/acme-corp|Acme Corp]]
---

# Meeting: Acme Q1 Planning

## Summary
[AI-generated summary]

## Action Items
- [ ] Send proposal by Friday - @andy
- [ ] Review budget numbers - @sarah
- [ ] Schedule follow-up - @bob

## Notes
[Full transcript below...]
```

---

## Task Categories

Using MoSCoW but with personal interpretation:

| Category | Rule |
|----------|------|
| **Must Do Today** | Client deadline, external commitment, time-sensitive |
| **Should Do Today** | Important for progress, internal deadline |
| **Could Do If Time** | Maintenance, nice-to-have, low stakes |
| **Waiting On Others** | Blocked - includes who and what I'm waiting for |

---

## Git Integration

The skill commits after processing:

```bash
git add -A && git commit -m "Process: morning routine [date]"
git push
```

**Why:**
- History of daily notes
- Sync across devices
- Backup

---

## What Took Iteration

Things that weren't right on first try:

1. **Too many sections** - Started with 10+ sections, cut to 6 that actually get used
2. **Task categories** - Tried Eisenhower, went back to MoSCoW (simpler)
3. **Commitment surfacing** - Initially too noisy, added filters for staleness
4. **Transcript storage** - Originally separate files, moved to collapsible in daily note
5. **Archive structure** - Started flat, added YYYY/MM-month for easier browsing

---

## Lessons Learned

**What works:**
- Brain dump must be truly unstructured - the more raw, the better AI extracts
- Top 3 priorities are the only thing that matters some days
- End of day reflection → next morning context is magic

**What doesn't work:**
- Over-engineering the template (just start simple)
- Trying to track everything (pick what matters)
- Skipping the brain dump (whole system falls apart)

---

## Adaptation Points

If copying this setup, you'll customize:

| Aspect | My Choice | Your Options |
|--------|-----------|--------------|
| Folder numbers | 00-05 scheme | Any numbering, or none |
| Client tracking | Separate projects | CRM, simple list, or skip |
| Entity linking | Separate People/Orgs folders | Inline mentions, or skip |
| Meeting capture | Granola | Otter, Fireflies, manual |
| Sync | Git + GitHub | iCloud, Dropbox, local |

---

*This is one implementation. The methodology stays the same; the structure adapts to your context.*
