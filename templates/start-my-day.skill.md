---
name: start-my-day
description: Morning routine that processes brain dump, creates daily note, and suggests priorities. Invoke with /start-my-day.
---

# Start My Day

Morning workflow: archive yesterday, create today.md, process brain dump, suggest priorities.

## Paths (CUSTOMIZE THESE)

```
Vault:     /Users/YOUR_USERNAME/path/to/your/vault
Today:     daily/today.md
Archive:   daily/archive/YYYY/MM-month/
Template:  daily/templates/daily-template.md
Projects:  projects/    (optional - for commitment surfacing)
```

---

## Workflow

### Phase 1: Health Check

```bash
# Verify vault access
ls "$VAULT_PATH" > /dev/null && echo "Vault: OK"
```

### Phase 2: Prepare Today.md

1. Check if `today.md` exists with old date
2. If old: archive to `daily/archive/YYYY/MM-month/YYYY-MM-DD.md`
3. Create fresh `today.md` from template
4. Carry forward incomplete `- [ ]` tasks from yesterday

### Phase 3: Process Brain Dump

If Brain Dump section has content:

1. **Extract action items** - Look for verbs:
   - "need to", "should", "have to", "must"
   - "send", "call", "email", "follow up"
   - "finish", "complete", "submit", "review"

2. **Identify context** - People, projects, deadlines mentioned

3. **Categorize tasks:**
   - Explicit deadlines today → Must Do Today
   - Important, flexible timing → Should Do Today
   - Nice to have → Could Do If Time
   - Waiting on someone → Waiting On Others

4. **Update Tasks section** with extracted items

### Phase 4: Surface Commitments (Optional)

If project notes exist, scan for:
- `- [ ]` open tasks
- "I owe" or "waiting on" mentions
- Recent commitments

Add to Active Commitments section with source.

### Phase 5: Suggest Priorities

Based on brain dump and commitments:
1. Identify items with deadlines
2. Identify high-stakes items
3. Suggest Top 3 priorities
4. Ask user to confirm or adjust

---

## Autonomy Rules

**Do automatically:**
- Archive yesterday's note
- Create new today.md
- Extract and categorize tasks
- Carry forward incomplete items

**Ask first:**
- Priority order (offer options)
- Ambiguous categorization
- Anything that deletes content

---

## Output

After running, report:

```markdown
# Good morning!

## Status
- [x] Yesterday archived to [path]
- [x] Today.md created for [date]
- [x] Brain dump processed: N tasks extracted
- [x] Carried forward: N incomplete items

## Suggested Top 3
1. [Based on deadlines/importance]
2. [Second priority]
3. [Third priority]

Confirm these priorities, or tell me what to adjust.
```

---

## Customization Notes

**To add meeting transcript processing:**
Add a Phase 1.5 that scans a `meetings/` or `Granola/` folder for new transcripts.

**To add commitment surfacing:**
Update the Projects path and add Phase 4 logic to scan your project notes.

**To change task categories:**
Replace MoSCoW (Must/Should/Could/Waiting) with your preferred system in Phase 3.
