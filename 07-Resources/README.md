---
title: Resources
type: meta
created: 2026-04-21
---

# 📚 Resources

Resources are reference materials designed for quick lookup—checklists, how-to guides, code snippets, templates, and quick-reference sheets.

## Purpose

- **Quick reference**: Find specific information fast
- **Reusable templates**: Standard formats for common tasks
- **Procedural knowledge**: Step-by-step guides
- **Code snippets**: Reusable code patterns
- **Checklists**: Ensure nothing is forgotten

## Structure

```
07-Resources/
├── Checklists/          # Task checklists
├── How-To-Guides/       # Step-by-step procedures
├── Code-Snippets/       # Reusable code
└── Quick-Reference/     # Lookup sheets
```

## Resource Types

### 1. Checklists

**Purpose**: Ensure completeness, reduce errors

**Examples:**
- `Weekly-Review-Checklist.md`
- `Code-Review-Checklist.md`
- `Pre-Launch-Checklist.md`
- `Daily-Standup-Checklist.md`
- `Meeting-Prep-Checklist.md`

**Format:**
```markdown
# Checklist Name

## Pre-[Task]
- [ ] Item 1
- [ ] Item 2
- [ ] Item 3

## During-[Task]
- [ ] Item 1
- [ ] Item 2

## Post-[Task]
- [ ] Item 1
- [ ] Item 2

## Notes
- [Additional context or tips]
```

**When to use:**
- Repeated tasks with multiple steps
- High-stakes tasks where errors are costly
- Onboarding or training scenarios

### 2. How-To Guides

**Purpose**: Step-by-step instructions for specific tasks

**Examples:**
- `How-To-Set-Up-SSH-Keys.md`
- `How-To-Write-Good-Commit-Messages.md`
- `How-To-Conduct-User-Interview.md`
- `How-To-Deploy-Application.md`

**Format:**
```markdown
# How To: [Task Name]

## What This Guide Covers
Brief description of what you'll learn

## Prerequisites
- Requirement 1
- Requirement 2

## Steps

### 1. [First Step]
Detailed instructions for first step

### 2. [Second Step]
Detailed instructions for second step

### 3. [Third Step]
Detailed instructions for third step

## Troubleshooting
- **Problem**: [Common issue]
  **Solution**: [How to fix]

## Related Guides
- [[Other-Guide]]
```

**When to use:**
- Infrequent tasks you might forget
- Complex procedures requiring specific order
- Knowledge you want to share with others
- Onboarding documentation

### 3. Code Snippets

**Purpose**: Reusable code patterns and solutions

**Examples:**
- `Python-File-Reading-Snippets.md`
- `Bash-One-Liners.md`
- `SQL-Common-Queries.md`
- `Git-Commands-Reference.md`

**Format:**
```markdown
# Code Snippets: [Language/Topic]

## Snippet Name

**Purpose**: What this does

**Code:**
```language
code here
```

**Usage:**
```language
example usage
```

**Notes:**
- Important considerations
- When to use this pattern

---

## Another Snippet Name
...
```

**When to use:**
- Code you use repeatedly
- Hard-to-remember syntax
- Configuration patterns
- Common utilities

### 4. Quick Reference

**Purpose**: Fast lookup for facts, commands, syntax

**Examples:**
- `Keyboard-Shortcuts-Reference.md`
- `Git-Commands-Quick-Reference.md`
- `Markdown-Syntax-Reference.md`
- `Regular-Expressions-Cheatsheet.md`

**Format:**
```markdown
# Quick Reference: [Topic]

## Category 1

| Command | Description | Example |
|---------|-------------|---------|
| `cmd1` | What it does | `cmd1 arg` |
| `cmd2` | What it does | `cmd2 arg` |

## Category 2

| Syntax | Meaning | Example |
|--------|---------|---------|
| `xyz` | What it is | `example` |
```

**When to use:**
- Information you look up frequently
- Commands or syntax reference
- Keyboard shortcuts
- Conversion tables, formulas

## Resources vs. Other Note Types

### Resources vs. Permanent Notes

**Resources**:
- ✅ Procedural ("how to")
- ✅ For quick reference
- ✅ Step-by-step
- ✅ Practical application

**Permanent Notes**:
- ✅ Conceptual ("what/why")
- ✅ For understanding
- ✅ Atomic ideas
- ✅ Theoretical knowledge

**Example:**

**Resource**: `How-To-Use-Spaced-Repetition.md`
- Steps to implement spaced repetition
- Tools to use (Anki, etc.)
- Sample schedule

**Permanent Note**: `20260421-Spaced-Repetition-Learning.md`
- Why spaced repetition works
- Cognitive science behind it
- Connections to memory formation

### Resources vs. Templates

**Resources**:
- Reference material
- Look up when needed
- Guide for specific tasks

**Templates**:
- Starting point for new notes
- Used when creating notes
- In `Templates/` folder

**Some overlap is okay**—a checklist template might exist in both places.

## Creating Good Resources

### Make Them Actionable

❌ **Vague:**
```markdown
# Code Review

Do code reviews well.
```

✅ **Specific:**
```markdown
# Code Review Checklist

## Functionality
- [ ] Does code do what it's supposed to?
- [ ] Are edge cases handled?
- [ ] Are errors handled gracefully?

## Code Quality
- [ ] Is code readable and clear?
- [ ] Are functions/methods single-purpose?
- [ ] Are names descriptive?
```

### Make Them Scannable

Use:
- ✅ Bulleted lists
- ✅ Numbered steps
- ✅ Tables
- ✅ Code blocks
- ✅ Clear headings
- ✅ Bold for key terms

Avoid:
- ❌ Long paragraphs
- ❌ Dense prose
- ❌ Buried important info

### Make Them Self-Contained

Resources should be usable without referencing other notes.

Include:
- Context (when to use this)
- Prerequisites (what you need first)
- Complete steps (don't assume knowledge)
- Examples (show, don't just tell)

## Resource Organization

### By Type (Recommended)

```
07-Resources/
├── Checklists/
│   ├── Weekly-Review.md
│   └── Code-Review.md
├── How-To-Guides/
│   ├── Git-Workflows.md
│   └── Deploy-Process.md
├── Code-Snippets/
│   ├── Python-Utils.md
│   └── Bash-Scripts.md
└── Quick-Reference/
    ├── Keyboard-Shortcuts.md
    └── Git-Commands.md
```

### By Domain (Alternative)

```
07-Resources/
├── Development/
│   ├── Git-Quick-Reference.md
│   ├── Deploy-Checklist.md
│   └── Code-Review-Guide.md
├── Writing/
│   ├── Blog-Post-Template.md
│   └── Editing-Checklist.md
└── Productivity/
    ├── Weekly-Review-Checklist.md
    └── Meeting-Prep-Guide.md
```

Choose the organization that makes finding things easiest for you.

## Naming Convention

**Format**: `Descriptive-Name.md`

**Examples:**
- ✅ `Weekly-Review-Checklist.md`
- ✅ `Git-Branching-Strategy.md`
- ✅ `Python-Virtual-Environments-Guide.md`
- ❌ `Checklist-1.md` (not descriptive)
- ❌ `guide.md` (too generic)

**Be specific** so you can find it later without opening the file.

## Maintaining Resources

### During Use

**When using a resource:**
- Note what's unclear or missing
- Fix errors immediately
- Add improvements after task completion

### During Weekly Review

- [ ] Update any resources you used this week
- [ ] Note any resources you wished existed

### During Monthly Review

- [ ] Review resources folder for outdated content
- [ ] Archive or update stale resources
- [ ] Create new resources for repeated tasks

## Linking Resources

### From Resources to Knowledge

```markdown
# How To: Implement Spaced Repetition

## Background Concepts
To understand why this works, see:
- [[Spaced-Repetition-Learning]]
- [[Forgetting-Curve]]

## Steps
...
```

### From Knowledge to Resources

```markdown
# 20260421-Spaced-Repetition-Learning

For practical application, see:
- [[How-To-Use-Anki-Effectively]]
- [[Spaced-Repetition-Schedule-Template]]
```

### From Projects to Resources

```markdown
# 2026-04-Website-Redesign/Project.md

## Resources
- [[Code-Review-Checklist]]
- [[Pre-Launch-Checklist]]
- [[Deploy-Process-Guide]]
```

## Common Resource Patterns

### The Standard Checklist
```markdown
# [Task] Checklist

## Purpose
What this checklist ensures

## Checklist

### Phase 1: Pre-[Task]
- [ ] Item
- [ ] Item

### Phase 2: During-[Task]
- [ ] Item
- [ ] Item

### Phase 3: Post-[Task]
- [ ] Item
- [ ] Item

## Notes
Additional tips or context
```

### The Step-by-Step Guide
```markdown
# How To: [Task]

## Overview
What you'll accomplish

## Prerequisites
- What you need

## Steps

1. **[Step 1]**: Detailed description
   ```
   Code or command example
   ```

2. **[Step 2]**: Detailed description

3. **[Step 3]**: Detailed description

## Troubleshooting
Common issues and solutions

## See Also
Related guides
```

### The Quick Reference
```markdown
# Quick Reference: [Topic]

## Most Common Operations

| Action | Command | Notes |
|--------|---------|-------|
| Do X | `command` | When to use |
| Do Y | `command` | When to use |

## Less Common But Useful

| Action | Command | Notes |
|--------|---------|-------|
| Do Z | `command` | When to use |

## See Also
- [[Full-Guide]]
```

## Examples

### Example Checklist

```markdown
# Weekly Review Checklist

## Purpose
Maintain second brain health and process weekly captures

## Checklist

### Inbox Processing (15 min)
- [ ] Review all items in `00-Inbox/`
- [ ] Process each: Move to appropriate folder
- [ ] Target: Get inbox to 10 or fewer items

### Note Creation (10 min)
- [ ] Transform 2-3 fleeting notes into permanent notes
- [ ] Add links to each new permanent note (1-2 minimum)
- [ ] Update relevant MOCs

### Project Updates (5 min)
- [ ] Add progress log to each active project
- [ ] Update next actions lists
- [ ] Note any blockers

## Tips
- Time-box to 30 minutes total
- Focus on processing, not perfecting
- Batch similar tasks together
```

### Example How-To Guide

```markdown
# How To: Create Effective Permanent Notes

## Overview
Transform fleeting or literature notes into permanent, evergreen notes.

## Prerequisites
- Source material (fleeting note, literature note, or idea)
- Understanding of the concept

## Steps

### 1. Ensure Understanding
Before creating permanent note, can you explain the concept
in your own words without looking at source?

### 2. Use Template
Create new note using permanent note template:
`Templates/template-permanent-note.md`

### 3. Write Title (YYYYMMDDHHMMSS-concept-name)
- Use timestamp prefix
- Descriptive concept name
- Example: `20260421150000-spaced-repetition-learning`

### 4. Write Main Idea
Express core concept in 2-3 sentences, your own words.

### 5. Add Context
Note where this idea came from and why it matters.

### 6. Add Supporting Details
Examples, evidence, elaboration.

### 7. Create Connections (Critical!)
Link to 1-2 existing notes minimum:
- What does this relate to?
- What does this support or contradict?
- What is this an example of?

### 8. Add to MOC
If relevant MOC exists (10+ related notes), add this note.

## Quality Check
- [ ] One atomic idea
- [ ] In your own words
- [ ] 1-2 links minimum
- [ ] Can stand alone
- [ ] Clear and specific title

## See Also
- [[09-Meta/Conventions]]
- [[03-Permanent/README]]
```

---

**Remember**: Resources are tools in your workshop—keep them sharp, well-organized, and ready to use. Create them when you find yourself doing the same task multiple times. Update them when you discover better ways. Your future self will thank you.
