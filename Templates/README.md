---
title: Templates
type: meta
created: 2026-04-21
---

# 📋 Templates

Templates provide consistent starting structures for different types of notes. They save time, ensure completeness, and maintain consistency across your second brain.

## Purpose

- **Consistency**: All notes of a type follow the same structure
- **Completeness**: Don't forget important sections
- **Speed**: Start writing immediately without thinking about structure
- **Quality**: Templates remind you of best practices

## Available Templates

### Core Templates (Created)

1. **`template-permanent-note.md`** - Most frequently used
   - For atomic, evergreen knowledge notes
   - Use: Creating notes in `03-Permanent/`

2. **`template-literature-note.md`** - Source material
   - For books, articles, courses, videos, podcasts
   - Use: Capturing external knowledge in `02-Literature/`

3. **`template-moc.md`** - Maps of content
   - For organizing 10+ related permanent notes
   - Use: Navigation indexes in `04-MOCs/`

4. **`template-daily-note.md`** - Daily captures
   - For daily logs, quick captures, reflections
   - Use: Daily notes in `01-Fleeting/Daily/`

5. **`template-project.md`** - Project tracking
   - For temporal, goal-oriented work
   - Use: Project notes in `05-Projects/`

### Optional Templates (Create as Needed)

You might create additional templates for:
- **Meeting notes**: Standard meeting structure
- **Area notes**: For tracking areas of responsibility
- **Resource templates**: Checklists, guides, snippets
- **Interview notes**: User interviews, research
- **Book review**: More detailed than literature note
- **Weekly review note**: If you want to create a note for each review

## Using Templates

### In Obsidian

**Method 1: Template Plugin (Core)**
1. Enable "Templates" core plugin
2. Set template folder: `Templates/`
3. Use command: Insert Template (Cmd/Ctrl + P → "Insert Template")
4. Choose template from list

**Method 2: Templater Plugin (Community)**
1. Install "Templater" community plugin
2. Set template folder: `Templates/`
3. Use command: Create new note from template
4. More powerful (dynamic dates, variables, scripts)

**Method 3: Manual Copy-Paste**
1. Open template file
2. Copy contents
3. Paste into new note
4. Fill in the blanks

### Template Variables

Templates use placeholder syntax:

**Obsidian Core Templates:**
```markdown
{{date:YYYY-MM-DD}}           → 2026-04-21
{{time:HH:mm:ss}}              → 14:30:22
{{title}}                      → Note title
```

**Templater Plugin:**
```markdown
<% tp.date.now("YYYY-MM-DD") %>        → 2026-04-21
<% tp.date.tomorrow("YYYY-MM-DD") %>   → 2026-04-22
<% tp.file.title %>                    → Note title
```

## Template Structure

### Good Template Structure

**Has clear sections:**
```markdown
---
Frontmatter (metadata)
---

# Title

## Section 1
[Purpose of this section]

Content area...

## Section 2
[Purpose of this section]

Content area...
```

**Has helpful prompts:**
```markdown
## Main Idea
> The core concept in your own words. One atomic idea.

[Write here...]
```

**Has examples when useful:**
```markdown
## Examples
- Example 1: [Concrete instance]
- Example 2: [Another instance]
```

### Template Frontmatter

**Minimal:**
```markdown
---
title:
created: {{date:YYYY-MM-DD}}
modified: {{date:YYYY-MM-DD}}
---
```

**Extended:**
```markdown
---
title:
type: permanent | literature | moc | project | daily
created: {{date:YYYY-MM-DD}} {{time:HH:mm:ss}}
modified: {{date:YYYY-MM-DD}} {{time:HH:mm:ss}}
tags:
  - status/draft
aliases:
  -
---
```

Use what's helpful for you—don't over-engineer.

## Creating Custom Templates

### When to Create a Template

✅ **Create template when:**
- You create the same type of note 3+ times
- You want consistency in structure
- You keep forgetting important sections
- You want to enforce best practices

❌ **Don't create template for:**
- One-off notes
- Highly variable content
- When flexibility is more important than structure

### Template Creation Process

1. **Create 2-3 notes manually** of the same type
2. **Notice the common structure** that emerges
3. **Identify essential sections** that every note should have
4. **Add helpful prompts** to guide content creation
5. **Create template file** in `Templates/`
6. **Test the template** by creating a real note with it
7. **Refine based on usage**

### Template Example: Meeting Notes

```markdown
---
title:
type: meeting
date: {{date:YYYY-MM-DD}}
attendees:
tags:
  - meeting
---

# Meeting: [Topic] - {{date:YYYY-MM-DD}}

## Context
**Date**: {{date:YYYY-MM-DD}}
**Time**: [Start time] - [End time]
**Attendees**: [Names]
**Purpose**: [Why this meeting]

## Agenda
1. [Item 1]
2. [Item 2]
3. [Item 3]

## Notes

### [Topic 1]
- Key points discussed
- Important information

### [Topic 2]
- Key points discussed
- Important information

## Decisions Made
1. **[Decision]** - Reasoning: [Why]
2. **[Decision]** - Reasoning: [Why]

## Action Items
- [ ] [Task] - Owner: [Name] - Due: [Date]
- [ ] [Task] - Owner: [Name] - Due: [Date]

## Follow-up
- Next meeting: [Date/Time]
- Related: [[Project]] | [[Area]]

## Notes for Future
[Anything worth remembering for next time]
```

## Template Best Practices

### Make Them Helpful, Not Restrictive

❌ **Too rigid:**
```markdown
## Main Idea (REQUIRED - MUST BE 2-3 SENTENCES)
[You must write exactly 2-3 sentences here or template police will find you]
```

✅ **Helpful guidance:**
```markdown
## Main Idea
> Express the core concept in 2-3 sentences

[Write naturally here...]
```

### Use Sections Wisely

**Essential sections:**
- Always needed
- Core to the note type
- Keep in every template

**Optional sections:**
- Use only when relevant
- Include with "(optional)" label
- Or comment out: `<!-- Optional: Add examples -->`

### Include Instructions Sparingly

❌ **Too much guidance:**
```markdown
## Main Idea
[This section should contain the primary concept that you are trying to
capture. Remember to write in your own words, not copying from the source.
Use 2-3 sentences typically, though you can use more if needed. Make sure
the idea is atomic and focused. Don't include multiple concepts here.]

Write here...
```

✅ **Concise guidance:**
```markdown
## Main Idea
> Core concept in your own words (2-3 sentences)

[Write here...]
```

### Use Placeholders

**For required information:**
```markdown
**Author**: [Author Name]
**Source**: [Book/Article Title]
**Date Read**: {{date:YYYY-MM-DD}}
```

**For lists:**
```markdown
## Key Takeaways
1. [First takeaway]
2. [Second takeaway]
3. [Third takeaway]
```

## Template Organization

### Current Structure (Simple)

```
Templates/
├── README.md
├── template-permanent-note.md
├── template-literature-note.md
├── template-moc.md
├── template-daily-note.md
├── template-project.md
└── [Your custom templates]
```

### Alternative Structure (If Many Templates)

```
Templates/
├── Core/
│   ├── template-permanent-note.md
│   ├── template-literature-note.md
│   └── template-moc.md
├── Work/
│   ├── template-meeting.md
│   ├── template-standup.md
│   └── template-project-retro.md
└── Personal/
    ├── template-book-review.md
    └── template-travel-log.md
```

Start simple, reorganize only if you have 10+ templates.

## Template Maintenance

### During Use

**When using a template:**
- Note sections you always delete
- Note sections you always add
- Note confusing prompts
- Update template after use if you found improvements

### During Monthly Review

- [ ] Review templates you used this month
- [ ] Update based on usage patterns
- [ ] Remove sections rarely used
- [ ] Add sections frequently needed
- [ ] Improve unclear guidance

### During Quarterly Review

- [ ] Review all templates
- [ ] Archive templates no longer used
- [ ] Create new templates for repeated patterns
- [ ] Ensure templates align with current conventions

## Obsidian Template Setup

### Core Templates Plugin (Built-in)

**Settings:**
1. Settings → Core Plugins → Enable "Templates"
2. Settings → Templates:
   - Template folder location: `Templates`
   - Date format: `YYYY-MM-DD`
   - Time format: `HH:mm:ss`

**Usage:**
- Command palette: "Templates: Insert template"
- Or assign hotkey

### Templater Plugin (Community - Advanced)

**Advantages:**
- Dynamic dates (yesterday, tomorrow, next week)
- User prompts (ask for input when creating)
- Scripts and automation
- More powerful variables

**Installation:**
1. Settings → Community Plugins → Browse → "Templater"
2. Install and enable
3. Settings → Templater:
   - Template folder: `Templates`
   - Enable trigger on new file (optional)

**Example Templater features:**
```markdown
Created: <% tp.date.now("YYYY-MM-DD HH:mm:ss") %>
Tomorrow: <% tp.date.tomorrow("YYYY-MM-DD") %>
Title: <% tp.file.title %>
Custom: <% tp.system.prompt("Enter project name") %>
```

## Template Quick Reference

| Template | Use Case | Folder | Frequency |
|----------|----------|--------|-----------|
| `template-permanent-note` | Atomic knowledge | `03-Permanent/` | High |
| `template-literature-note` | Source material | `02-Literature/` | Medium |
| `template-moc` | Navigation index | `04-MOCs/` | Low |
| `template-daily-note` | Daily log | `01-Fleeting/Daily/` | Daily |
| `template-project` | Project tracking | `05-Projects/` | Medium |

## Common Mistakes

❌ **Too many templates**
- Template for every tiny variation
- ✅ Start with 5-6 core templates

❌ **Templates too complex**
- 50 fields and sections
- ✅ Keep essential sections only

❌ **Never updating templates**
- Templates drift from actual usage
- ✅ Update monthly based on usage

❌ **Templates as rules**
- Forcing all notes to fit template exactly
- ✅ Templates as starting points, not straitjackets

❌ **Skipping templates for speed**
- "I'll just free-form this one"
- ✅ Templates save time and ensure quality

## Tips for Template Success

### Start with Core Templates

Use the 5 provided templates:
1. Permanent note (most used)
2. Literature note
3. MOC
4. Daily note
5. Project note

These cover 80% of use cases.

### Customize Gradually

- Use templates as-is initially
- Note what doesn't work
- Adjust monthly
- Let your templates evolve with your practice

### Don't Over-Template

**Template these:**
- Permanent notes
- Literature notes
- MOCs
- Projects
- Daily notes

**Don't template these:**
- Quick captures (inbox)
- One-off notes
- Experimental notes
- Highly creative work

### Make Templates Easy to Access

**Assign hotkeys:**
- Insert permanent note template: `Cmd/Ctrl + Shift + P`
- Create daily note: `Cmd/Ctrl + D`

**Use quick commands:**
- Templater can auto-apply templates based on folder
- Daily notes can auto-use template

---

**Remember**: Templates are tools to help you create better notes faster, not rules to constrain your thinking. Start with the provided templates, use them consistently, and adapt them to fit how you actually work. The best template is one you'll actually use.

**Quick Start:**
1. Enable Templates plugin in Obsidian
2. Set folder to `Templates/`
3. Try creating a permanent note using the template
4. Adjust templates monthly based on usage
