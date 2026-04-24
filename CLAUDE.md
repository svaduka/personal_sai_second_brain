# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **personal knowledge management system**—a Zettelkasten-inspired second brain built with markdown files, designed for use with Obsidian. The system captures, processes, and connects ideas through a structured workflow and linking strategy.

## Architecture & Philosophy

### Core Methodology: Zettelkasten
- **Atomic notes**: One idea per note
- **Progressive summarization**: Ideas flow from rough captures to refined knowledge
- **Linking over organizing**: Connections matter more than folder hierarchy
- **Emergence**: Structure evolves naturally through connections

### Note Progression Workflow
```
Quick Capture → Fleeting Note → Literature Note → Permanent Note → Connected in MOC
```

- **Fleeting** (`01-Fleeting/`): Quick captures, daily notes, rough thoughts
- **Literature** (`02-Literature/`): Notes from external sources (books, articles, courses)
- **Permanent** (`03-Permanent/`): Refined atomic ideas in your own words—the core knowledge base
- **MOCs** (`04-MOCs/`): Maps of Content that organize 10+ related permanent notes

### Directory Structure & Purpose

| Directory | Purpose | Organization |
|-----------|---------|--------------|
| `00-Inbox/` | Unsorted captures, processed weekly | Flat, temporary |
| `01-Fleeting/` | Daily notes, quick thoughts | Nested by date |
| `02-Literature/` | Source material notes | Shallow nesting by type |
| `03-Permanent/` | **Core Zettelkasten**—atomic knowledge notes | Flat, linked |
| `04-MOCs/` | Maps of Content for navigation | Flat |
| `05-Projects/` | Active temporal projects | Nested by project folder |
| `06-Areas/` | Ongoing responsibilities | Shallow nesting |
| `07-Resources/` | Checklists, guides, code snippets | Nested by type |
| `08-Archive/` | Completed/inactive content | Nested by year/month |
| `09-Meta/` | System documentation | Flat |
| `Templates/` | Note templates | Flat |

**Key principle**: `03-Permanent/` should remain flat—organization happens through links and MOCs, not folder hierarchies.

## Strict Naming Conventions

### Permanent Notes
**Format**: `YYYYMMDDHHMMSS-descriptive-title.md`
- Timestamp ensures uniqueness and chronological sorting
- Use lowercase with hyphens
- Example: `20260421143022-spaced-repetition-learning.md`

### Literature Notes
**Format**:
- Books: `Author-Year-Book-Title.md` (e.g., `Newport-2016-Deep-Work.md`)
- Articles: `Source-YYYY-MM-DD-Article-Title.md` (e.g., `Medium-2026-04-15-Building-Second-Brain.md`)
- Courses: `Platform-Instructor-Course-Name.md`

### Maps of Content (MOCs)
**Format**: `Topic-Name-MOC.md`
- **Always** end with `-MOC` suffix
- Example: `Learning-Methods-MOC.md`

### Projects
**Format**: `YYYY-MM-Project-Name/` (folder with date prefix)
- Example: `2026-04-Website-Redesign/`

### Daily Notes
**Format**: `YYYY-MM-DD.md` (ISO 8601 date)
- Location: `01-Fleeting/Daily/`

## Linking Strategy

### Required Linking Practice
- Every permanent note **must link to 1-2 other notes minimum**
- Use Obsidian wikilinks: `[[Note Title]]` or `[[Note Title|Display Text]]`
- Prefer links over tags for conceptual connections

### Link Types (use contextually)
- **Related to**: General connection
- **Example of**: Specific instance of a concept
- **Contradicts**: Opposing ideas
- **Supports**: Reinforcing ideas
- **Part of**: Links to parent MOC

### When to Create a MOC
- You have **10+ related notes** on a topic
- Navigation is becoming difficult
- A topic is becoming a "hub" with many connections

## Tags (Use Sparingly)

Use tags for metadata, not for connections (use links instead):

**Status tags**:
- `#status/draft` - Work in progress
- `#status/evergreen` - Refined, stable knowledge

**Type tags**:
- `#type/literature` - Source material
- `#type/project` - Project-related
- `#type/moc` - Map of content

**Rule**: If using a tag 10+ times, create a MOC instead.

## Common Operations

### Creating a New Permanent Note
1. Use template: `Templates/template-permanent-note.md`
2. Generate filename: `YYYYMMDDHHMMSS-descriptive-title.md`
3. Place in: `03-Permanent/`
4. **Critical**: Add links to at least 1-2 existing notes
5. Fill out Context, Main Idea, Connections sections

### Creating a New MOC
1. Ensure you have 10+ related permanent notes
2. Use template: `Templates/template-moc.md`
3. Name: `Topic-Name-MOC.md`
4. Place in: `04-MOCs/`
5. Structure: Overview → Core Concepts → Deep Dives → Related MOCs → Open Questions
6. Update Master Index: `04-MOCs/00-Master-Index.md`

### Processing Inbox
1. Review items in `00-Inbox/`
2. For each item, decide:
   - Still relevant? If no → delete or archive
   - If yes → categorize and move:
     - Quick thought → Make permanent or discard
     - Source material → `02-Literature/`
     - Refined idea → `03-Permanent/`
     - Project-related → `05-Projects/`
     - Reference → `07-Resources/`
3. Target: Keep inbox under 20 items, process weekly to under 10

### Creating a Daily Note
1. Use template: `Templates/template-daily-note.md`
2. Name: `YYYY-MM-DD.md`
3. Place in: `01-Fleeting/Daily/`
4. Capture quick thoughts, to-dos, reflections

### Archiving a Project
1. Document final outcomes in project folder
2. Extract learnings into permanent notes with proper timestamps
3. Update project status to "Completed" or "Cancelled"
4. Move folder to: `08-Archive/YYYY/MM/`

## Review Cadences

### Daily (5 min)
- Review today's daily note
- Capture remaining thoughts
- Note tomorrow's priority

### Weekly (30 min, non-negotiable)
- Process inbox to < 10 items
- Create 2-3 permanent notes from fleeting notes
- Update active project notes
- Create/update links between notes

### Monthly (60 min)
- Review all MOCs for completeness
- Archive completed projects
- Check for orphaned notes (no incoming links)
- Identify emerging topics for new MOCs
- Update Master Index statistics

### Quarterly (2 hours)
- Review system conventions (`09-Meta/Conventions.md`)
- Assess what's working and what isn't
- Refactor large MOCs (split if > 50 notes)
- Clean up archive
- Plan next quarter

## Quality Requirements

### For Permanent Notes
- [ ] Descriptive, specific title with timestamp prefix
- [ ] Contains one atomic idea
- [ ] Written in your own words (not copy-pasted)
- [ ] Links to 1-2 related notes minimum
- [ ] Explains context (origin of the idea)
- [ ] Tag: `#status/draft` → `#status/evergreen` when refined

### For MOCs
- [ ] Name ends with `-MOC`
- [ ] Covers 10+ related notes
- [ ] Has overview section explaining the map's scope
- [ ] Organizes notes into logical groups
- [ ] Links to related MOCs
- [ ] Updated when new related notes are created

### For Literature Notes
- [ ] Follows source naming convention
- [ ] Includes bibliographic information
- [ ] Summarizes key takeaways
- [ ] Links to permanent notes created from it

## Anti-Patterns to Avoid

❌ **Over-organizing**: Don't create deep folder hierarchies in `03-Permanent/`—use links and MOCs instead

❌ **No links**: Never create permanent notes in isolation—they must connect to existing knowledge

❌ **Inbox neglect**: Don't let inbox grow beyond 20 items—process weekly

❌ **Premature MOCs**: Don't create MOCs with fewer than 10 notes—let structure emerge naturally

❌ **Copy-paste literature notes**: Don't copy without processing—permanent notes must be in your own words

❌ **Tag explosion**: Don't create 50+ tags—use links for connections, tags only for metadata

## Key Reference Documents

- **System Conventions**: `09-Meta/Conventions.md`—detailed naming, linking, and organizational rules
- **Review Process**: `09-Meta/Review-Process.md`—detailed review workflows and checklists
- **Master Index**: `04-MOCs/00-Master-Index.md`—central navigation hub

## Working with Claude Code

When helping with this knowledge base:

1. **Always follow naming conventions** exactly—timestamps, hyphens, proper suffixes
2. **Enforce linking requirements**—every permanent note needs 1-2 links minimum
3. **Respect flat architecture**—don't create subfolders in `03-Permanent/`
4. **Use templates**—they ensure consistency and completeness
5. **Check for existing notes**—use grep/glob to find related notes before creating new ones
6. **Update the Master Index**—when creating new MOCs, add them to `04-MOCs/00-Master-Index.md`
7. **Maintain atomicity**—one clear idea per permanent note
8. **Process, don't just organize**—when working with inbox, help transform ideas into permanent notes with proper connections

## System Health Indicators

| Metric | Healthy | Warning | Action Needed |
|--------|---------|---------|---------------|
| Inbox items | < 10 | 10-20 | > 20 |
| Days since last permanent note | < 7 | 7-14 | > 14 |
| Orphaned notes | < 5% | 5-10% | > 10% |
| Active projects | 1-5 | 6-8 | > 8 |
