# Setup Guide

Complete setup from scratch. Pick your path and follow the steps.

---

## Choose Your Path

| Path | What You Need | Setup Time | Daily Effort |
|------|---------------|------------|--------------|
| **A: Full Automation** | Obsidian + VS Code + Claude Code | 2-3 hours | 5 min (automated) |
| **B: Obsidian Only** | Obsidian + claude.ai browser | 1 hour | 10 min (copy/paste) |
| **C: Minimal** | Any text editor + claude.ai | 15 min | 10 min (copy/paste) |

**Recommendation:** Start with Path C to learn the methodology. Upgrade to A when you're hooked.

---

# Path A: Full Automation

## A1: Install Obsidian

[Obsidian](https://obsidian.md) is a note-taking app that stores everything as plain markdown files.

1. Download from [obsidian.md](https://obsidian.md)
2. Install and open
3. Create a new vault:
   - Click "Create new vault"
   - Name it (e.g., "Notes" or "Second Brain")
   - Choose location (Documents folder works)

## A2: Install VS Code

[VS Code](https://code.visualstudio.com) is the interface for Claude Code.

1. Download from [code.visualstudio.com](https://code.visualstudio.com)
2. Install and open

## A3: Install Claude Code

Claude Code is an AI assistant that reads and writes files in your vault.

**Via VS Code Extension:**
1. Open VS Code
2. Click Extensions (puzzle piece icon, left sidebar)
3. Search "Claude Code"
4. Install the Anthropic extension
5. Sign in with your Anthropic account

**Via Command Line (alternative):**
```bash
npm install -g @anthropic-ai/claude-code
claude login
```

## A4: Create Folder Structure

Open your vault and create:

```
your-vault/
├── daily/
│   ├── today.md
│   ├── templates/
│   │   └── daily-template.md
│   └── archive/
│       └── 2026/
│           └── 01-january/
├── projects/           # Optional: for commitment tracking
└── CLAUDE.md           # AI configuration
```

## A5: Add Template Files

Copy from this repo:
- [templates/daily-template.md](../templates/daily-template.md) → `daily/templates/`
- [templates/CLAUDE.md.example](../templates/CLAUDE.md.example) → vault root (rename to `CLAUDE.md`)

Edit `CLAUDE.md` to match your vault path.

## A6: Create the Skill

```bash
mkdir -p ~/.claude/skills/start-my-day
```

Copy [templates/start-my-day.skill.md](../templates/start-my-day.skill.md) to `~/.claude/skills/start-my-day/SKILL.md`

**Edit the Paths section** to match your vault location.

## A7: Set Up Voice Capture

Pick one:

| Method | How |
|--------|-----|
| iPhone Voice Memos | Record → transcribe → paste |
| macOS Dictation | Cmd+Cmd → speak → it types |
| Google Docs Voice | Tools → Voice Typing |
| Otter.ai | Records and transcribes |
| Just type | Skip voice, type thoughts |

## A8: Optional - Granola for Meetings

[Granola](https://granola.so) transcribes your meetings automatically.

1. Download from [granola.so](https://granola.so)
2. In Obsidian: Settings → Community Plugins → Browse → "Granola Sync"
3. Configure to save to `Granola/` folder

## A9: Test It

1. Open VS Code in your vault
2. Start Claude Code
3. Type: `/start-my-day`
4. Paste a test brain dump when prompted
5. Review the structured output

---

# Path B: Obsidian Only

No Claude Code - you'll copy/paste to claude.ai instead.

## B1: Install Obsidian

Same as A1 above.

## B2: Create Folder Structure

```
your-vault/
├── daily/
│   ├── today.md
│   ├── templates/
│   │   └── daily-template.md
│   └── archive/
```

## B3: Add Template

Copy [templates/daily-template.md](../templates/daily-template.md) to `daily/templates/`

## B4: Daily Workflow

Each morning:

1. Create `today.md` from template (or duplicate yesterday's)
2. Do your brain dump (voice or typing) into the Brain Dump section
3. Open [claude.ai](https://claude.ai)
4. Paste this prompt:

```
Here's my morning brain dump. Please:
1. Extract all action items
2. Categorize as: Must Do Today / Should Do Today / Could Do If Time / Waiting On Others
3. Suggest my Top 3 priorities for today
4. Format as markdown I can paste into my daily note

Brain dump:
[paste your brain dump]
```

5. Copy Claude's response into your daily note

---

# Path C: Minimal

No Obsidian, no special tools. Just a folder.

## C1: Create a Folder

Anywhere on your computer:

```
daily-notes/
├── today.md
└── archive/
```

## C2: Create today.md

Use any text editor. Copy the structure from [templates/daily-template.md](../templates/daily-template.md).

## C3: Daily Workflow

Same as Path B step 4 - paste brain dump to claude.ai, get structured output, paste back.

## C4: Archive Yesterday

Each morning, rename `today.md` to `YYYY-MM-DD.md` and move to `archive/`. Create fresh `today.md`.

---

# Voice Capture Deep Dive

## iPhone

1. Open Voice Memos
2. Record your brain dump (2-3 min)
3. Tap the recording → three dots → "Copy Transcript" (iOS 18+)
4. Paste into today.md

**Pre-iOS 18:** Use Whisper or a transcription app.

## Mac

1. Position cursor in Brain Dump section
2. Press Cmd+Cmd (or fn fn on newer Macs)
3. Speak - it types as you talk
4. Click Done when finished

## Web-Based

1. Open [Google Docs](https://docs.google.com)
2. Tools → Voice Typing
3. Click microphone, speak
4. Copy text to today.md

---

# Customization

Once you're using it daily, customize:

| Aspect | Options |
|--------|---------|
| Task categories | MoSCoW (default), Eisenhower, Energy-based, Context (@calls, @computer) |
| Folder structure | Match your existing organization |
| Commitment sources | Add project MOCs, CRM links, people notes |
| Meeting integration | Granola, Otter, Fireflies, manual |

See [examples/implementation-example.md](../examples/implementation-example.md) for a real-world setup.

---

# Troubleshooting

**Claude can't find my vault**
- Check the path in SKILL.md (use absolute path like `/Users/you/Documents/Vault`)

**Tasks aren't extracting well**
- Use more action verbs: "need to send", "should call", "have to finish"
- Be explicit about deadlines: "by Friday", "before the meeting"

**I forget to do this**
- Set a morning alarm: "Brain dump time"
- Stack with existing habit: after coffee, before email

**Too overwhelming**
- Start with just Top 3 priorities
- Add task categories after a week
- Add end-of-day reflection after two weeks

---

*Next: [Daily usage cheat sheet](cheat-sheet.md)*
