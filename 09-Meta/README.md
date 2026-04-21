---
title: Meta (System Documentation)
type: meta
created: 2026-04-21
---

# 🛠️ Meta - System Documentation

The Meta folder contains documentation about the second brain system itself—conventions, workflows, reviews, and any system improvements.

## Purpose

- **System documentation**: How this second brain works
- **Conventions reference**: Naming, linking, organizing rules
- **Workflow guides**: Review processes and best practices
- **System evolution**: Track changes and improvements
- **Troubleshooting**: Solutions to common problems

## What Lives Here

✅ **Meta content includes:**
- **Conventions.md**: Naming, linking, tagging rules
- **Review-Process.md**: Daily, weekly, monthly, quarterly reviews
- **System-Evolution.md**: Changelog of system improvements
- **Troubleshooting.md**: Common problems and solutions
- **Statistics.md**: System metrics and growth tracking
- **Quarterly-Review-YYYY-QX.md**: Quarterly review notes
- **Lessons-Learned.md**: What worked, what didn't

❌ **Not meta content:**
- **General knowledge**: Goes in `03-Permanent/`
- **Project documentation**: Goes in `05-Projects/`
- **How-to guides** (for external tasks): Goes in `07-Resources/`
- **Templates**: Goes in `Templates/`

## Core Meta Documents

### 1. Conventions.md
**Status**: Already created ✅

**Contains:**
- Naming conventions for all note types
- Linking strategy and principles
- Tagging strategy
- Folder structure rules
- Note progression workflow
- Review processes
- Common pitfalls

**When to update:**
- Quarterly reviews
- When changing a convention
- When adding new note types
- When you notice confusing patterns

### 2. Review-Process.md
**Status**: Already created ✅

**Contains:**
- Daily review (5 min)
- Weekly review (30 min)
- Monthly review (60 min)
- Quarterly review (2 hours)
- Checklists for each review
- Best practices

**When to update:**
- Review process isn't working
- Found more efficient workflow
- Need to add/remove steps

### 3. System-Evolution.md
**Status**: Create as needed

**Purpose**: Track how the system changes over time

**Contents:**
```markdown
# System Evolution

## 2026-Q2

### Changes Made
- Added [new convention/folder/workflow]
- Reason: [Why this change]
- Impact: [What changed]

### What Worked
- [Practice that's helping]

### What Didn't Work
- [Practice abandoned]
- Why: [Reason]

## 2026-Q1
...
```

**When to update:**
- Quarterly reviews
- After major system changes

### 4. Troubleshooting.md
**Status**: Create as needed

**Purpose**: Solutions to common problems

**Contents:**
```markdown
# Troubleshooting

## Inbox Overwhelming (20+ items)

**Problem**: Inbox has grown beyond manageable size

**Solutions**:
1. Time-box 30 min for emergency processing
2. Lower standards temporarily (archive if unsure)
3. Focus on highest-value items first
4. Schedule dedicated processing sessions

## Can't Find Notes

**Problem**: Created a note but can't locate it

**Solutions**:
1. Use Obsidian Quick Switcher (Cmd/Ctrl + O)
2. Search content (Cmd/Ctrl + Shift + F)
3. Check graph view for connections
4. Review relevant MOC

## Too Many Drafts, Nothing Evergreen

**Problem**: All notes tagged #status/draft

**Solutions**:
1. Pick 1-2 drafts per weekly review to refine
2. Lower bar for "evergreen" (done is better than perfect)
3. Focus on links, not polish
4. Some drafts are okay—don't force premature refinement

[More problems and solutions...]
```

**When to update:**
- Encounter new problem
- Find better solution
- During reviews

### 5. Statistics.md
**Status**: Create as needed

**Purpose**: Track system growth and health

**Contents:**
```markdown
# System Statistics

## 2026-04-21 (System Start)

### Note Counts
- Permanent Notes: 0
- MOCs: 1 (Master Index)
- Active Projects: 0
- Areas: 0
- Literature Notes: 0
- Templates: 6

### Health Metrics
- Inbox Items: 0
- Orphaned Notes: 0
- Last Weekly Review: 2026-04-21
- Last Monthly Review: 2026-04-21

### Goals for Next Month
- Create 10+ permanent notes
- Process inbox weekly
- Establish daily note habit

## 2026-05-21 (1 Month)
[Update stats monthly]
...
```

**When to update:**
- Monthly reviews (recommended)
- Track note count, review consistency, etc.

## Meta Folder Organization

### Simple Structure (Recommended)

```
09-Meta/
├── README.md                    # This file
├── Conventions.md               # ✅ Created
├── Review-Process.md            # ✅ Created
├── System-Evolution.md          # Create when needed
├── Troubleshooting.md           # Create when needed
├── Statistics.md                # Create when needed
├── Quarterly-Review-2026-Q2.md  # Create quarterly
├── Quarterly-Review-2026-Q3.md
└── ...
```

### Extended Structure (If Needed Later)

```
09-Meta/
├── Core/
│   ├── Conventions.md
│   ├── Review-Process.md
│   └── Troubleshooting.md
├── Quarterly-Reviews/
│   ├── 2026-Q2.md
│   ├── 2026-Q3.md
│   └── ...
└── Evolution/
    ├── System-Evolution.md
    └── Statistics.md
```

Start simple, add structure only if needed.

## Using Meta Documentation

### When Starting

**Read these first:**
1. Main `README.md` (root folder)
2. `09-Meta/Conventions.md`
3. `09-Meta/Review-Process.md`

**Then:**
- Explore folder READMEs as you use each folder
- Reference conventions when creating notes
- Use review checklists

### During Regular Use

**Reference Meta documents when:**
- Creating new notes (check naming conventions)
- Processing inbox (follow workflows)
- Doing reviews (use checklists)
- Something isn't working (check troubleshooting)
- Considering changes (review conventions first)

### During System Improvement

**Update Meta documents when:**
- Conventions change
- New workflows discovered
- Problems solved
- Quarterly review identifies improvements

## Meta Document Best Practices

### Keep Them Current

❌ **Outdated documentation is worse than none**
- Leads to confusion
- Creates inconsistency
- Wastes time

✅ **Update during quarterly reviews**
- Review each meta document
- Update outdated information
- Add new learnings
- Archive obsolete sections

### Make Them Actionable

❌ **Vague:**
```markdown
# Conventions
Use good naming conventions for notes.
```

✅ **Specific:**
```markdown
# Conventions

## Permanent Notes
Format: YYYYMMDDHHMMSS-descriptive-title.md
Example: 20260421150000-spaced-repetition-learning.md
```

### Make Them Scannable

Use:
- Clear headings
- Bulleted lists
- Tables
- Code blocks
- Examples

### Make Them Living Documents

**Meta docs should evolve:**
- Add lessons learned
- Update conventions that aren't working
- Simplify complex processes
- Remove obsolete practices

**Version or track changes:**
```markdown
---
created: 2026-04-21
updated: 2026-07-15
---

## Change Log
- 2026-07-15: Simplified naming convention for literature notes
- 2026-06-01: Added troubleshooting section
- 2026-04-21: Initial creation
```

## Quarterly Review Template

Create one each quarter in this folder.

**File**: `Quarterly-Review-2026-Q2.md`

**Template:**
```markdown
---
title: Quarterly Review Q2 2026
date: 2026-06-30
type: meta
---

# Quarterly Review - Q2 2026

## System Assessment

### What's Working Well
- [Practice/workflow that's effective]
- [What's helping the most]

### What's Not Working
- [Friction points]
- [Abandoned practices]

### Adjustments to Make
- [Changes to conventions]
- [Process improvements]

## Statistics

### Note Growth
- Permanent Notes: Start [X] → End [Y] (Growth: +Z)
- MOCs: [count]
- Projects Completed: [count]

### Health Metrics
- Weekly reviews completed: X/13
- Average inbox size: [number]
- Orphaned notes: [count]

## Convention Changes

### Changes Made
- [What changed]
- Reason: [Why]

## Next Quarter Focus

### Goals
- [Goal 1]
- [Goal 2]

### System Improvements
- [Planned improvement 1]
- [Planned improvement 2]

## Reflections
[Open-ended thoughts about the system and how it's serving you]
```

## Meta Linking

### From Meta to Knowledge

Meta documents can reference permanent notes as examples:

```markdown
## Permanent Note Example

A good permanent note looks like:
[[20260421-Example-Note]]
```

### From Knowledge to Meta

Permanent notes don't typically link to meta, but can:

```markdown
## Metadata
Created using: [[09-Meta/Conventions]]
```

### Between Meta Documents

Cross-reference frequently:

```markdown
For naming conventions, see: [[09-Meta/Conventions]]
For review workflows, see: [[09-Meta/Review-Process]]
```

## Common Meta Documents You Might Add

As your system grows, consider adding:

### Learning.md
Lessons learned about knowledge management itself

### Obsidian-Setup.md
Your Obsidian configuration, plugins, settings

### Backup-Strategy.md
How you backup your second brain

### Sharing-Guidelines.md
If you share your knowledge publicly, what's public vs. private

### Templates-Guide.md
How to use and customize templates

### Migration-Notes.md
If moving from another system, document the process

## Meta Document Maintenance

### During Monthly Review
- [ ] Quick scan of meta documents
- [ ] Add any new troubleshooting solutions
- [ ] Note any conventions that aren't working

### During Quarterly Review
- [ ] Deep review of all meta documents
- [ ] Update conventions if needed
- [ ] Create quarterly review document
- [ ] Update system evolution log
- [ ] Review statistics

## Quick Start

**First week:**
1. Read `README.md` (root)
2. Read `09-Meta/Conventions.md`
3. Skim `09-Meta/Review-Process.md`

**First month:**
1. Reference conventions when creating notes
2. Use review process checklists
3. Note any confusion or friction

**First quarter:**
1. Create first quarterly review
2. Update conventions based on experience
3. Start tracking statistics if helpful

---

**Remember**: Meta documentation exists to serve you, not the other way around. Start minimal, add complexity only as needed, and update quarterly to keep it relevant. The best system documentation is the one you'll actually use.

**Current Meta Status:**
- ✅ Conventions.md created
- ✅ Review-Process.md created
- ⏳ Other documents: Create as needed
