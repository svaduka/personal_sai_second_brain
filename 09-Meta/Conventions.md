---
title: System Conventions
type: meta
created: 2026-04-21
updated: 2026-04-21
---

# System Conventions

This document defines the naming rules, linking strategies, and organizational principles for this second brain. Following these conventions ensures consistency and makes the system easier to navigate and maintain.

## 📝 Naming Conventions

### Permanent Notes
**Format**: `YYYYMMDDHHMMSS-descriptive-title.md`

- **Timestamp prefix**: Ensures uniqueness and chronological sorting
- **Descriptive title**: Use lowercase with hyphens, be specific
- **Examples**:
  - ✅ `20260421143022-spaced-repetition-learning.md`
  - ✅ `20260421150000-compound-interest-knowledge.md`
  - ❌ `note.md` (too vague)
  - ❌ `my-thoughts-2026.md` (not specific enough)

**When to use**: For refined atomic ideas in `03-Permanent/`

### Literature Notes
**Format**: `Author-Year-Title.md` or `Source-YYYY-MM-DD-Title.md`

- **Book**: `Author-Year-Book-Title.md`
  - Example: `Newport-2016-Deep-Work.md`
- **Article**: `Source-YYYY-MM-DD-Article-Title.md`
  - Example: `Medium-2026-04-15-Building-Second-Brain.md`
- **Course**: `Platform-Instructor-Course-Name.md`
  - Example: `Coursera-Andrew-Ng-Machine-Learning.md`
- **Video**: `Platform-Creator-YYYY-MM-DD-Title.md`
  - Example: `YouTube-Ali-Abdaal-2026-04-10-Note-Taking.md`

**When to use**: For notes from external sources in `02-Literature/`

### Maps of Content (MOCs)
**Format**: `Topic-Name-MOC.md`

- **Always end with `-MOC`**: Makes them easily identifiable
- **Topic first**: Use the main topic or domain name
- **Examples**:
  - ✅ `Learning-Methods-MOC.md`
  - ✅ `Distributed-Systems-MOC.md`
  - ✅ `Personal-Productivity-MOC.md`
  - ❌ `MOC-Learning.md` (wrong order)
  - ❌ `Learning-Index.md` (should use -MOC suffix)

**When to use**: When you have 10+ related permanent notes on a topic

### Projects
**Format**: `YYYY-MM-Project-Name/` (folder)

- **Date prefix**: Year-month when project started
- **Folder structure**: Each project gets its own folder
- **Examples**:
  - ✅ `2026-04-Website-Redesign/`
  - ✅ `2026-03-Learn-Rust/`
  - ❌ `website-project/` (no date prefix)
  - ❌ `2026-Project/` (too vague)

**When to use**: For temporal projects in `05-Projects/`

### Daily Notes
**Format**: `YYYY-MM-DD.md`

- **ISO 8601 date format**: Standard, sortable
- **Location**: `01-Fleeting/Daily/`
- **Examples**:
  - ✅ `2026-04-21.md`
  - ❌ `April-21-2026.md` (non-standard format)
  - ❌ `21-04-2026.md` (ambiguous day/month order)

**When to use**: For daily captures and logs

### General File Naming Rules

- **Use lowercase**: Except for acronyms (MOC, API, etc.)
- **Use hyphens**: Not underscores or spaces
- **Be specific**: Descriptive titles help future you
- **Keep it concise**: Aim for 3-7 words in the title
- **No special characters**: Avoid `/`, `\`, `:`, `*`, `?`, `"`, `<`, `>`, `|`

## 🔗 Linking Strategy

### Basic Linking

**Wikilinks (preferred)**:
```markdown
[[Note Title]]
[[Note Title|Display Text]]
```

**Why wikilinks?**
- Obsidian-native
- Auto-complete friendly
- Easier to refactor
- Shows unlinked mentions

### Linking Principles

1. **Minimum connections**: Every permanent note should link to 1-2 other notes
   - If you can't link to anything, the note might not belong in permanent yet

2. **Link liberally**: Create connections as you write
   - Link when you reference an idea
   - Link when you see relationships
   - Link when you want to explore further

3. **Bidirectional linking**: Think about forward and backward links
   - Forward: This idea builds on...
   - Backward: Check backlinks panel to see what references this note

4. **Link types** (use in context):
   - **Related to**: General connection
   - **Example of**: Specific instance of a concept
   - **Contradicts**: Opposing ideas
   - **Supports**: Reinforcing ideas
   - **Part of**: Hierarchical relationship (note → MOC)

### When to Create MOCs

- You have **10+ related notes** on a topic
- Navigation is becoming difficult
- You're starting to forget what you've written
- A topic is becoming a "hub" for many notes

### MOC Organization

**Structure a MOC like this:**
1. **Overview**: What this map covers
2. **Core Concepts**: Foundational ideas (3-7 links)
3. **Deep Dives**: Detailed explorations (organized by sub-topic)
4. **Related MOCs**: Connections to other maps
5. **Open Questions**: What to explore next

## 🏷️ Tagging Strategy

**Use tags sparingly**—prefer links for connections.

### Status Tags
- `#status/draft` - Work in progress
- `#status/evergreen` - Refined, stable knowledge
- `#status/archive` - Outdated or no longer relevant

### Type Tags
- `#type/literature` - Source material note
- `#type/project` - Project-related
- `#type/moc` - Map of content
- `#type/meta` - System documentation

### Domain Tags (optional)
- Use domain tags only if you have many notes in distinct domains
- Example: `#domain/technology`, `#domain/writing`
- Prefer MOCs over domain tags

**Best practice**: If you're using a tag more than 10 times, consider creating a MOC instead.

## 📁 Folder Structure Rules

### Flat Hierarchy

- **03-Permanent/** should be mostly flat
  - Don't create deep subfolders
  - Use links and MOCs for organization
  - Exception: If you have 1000+ notes, consider year-based subfolders

### Folder Purposes

| Folder | Flat/Nested | Notes |
|--------|-------------|-------|
| `00-Inbox/` | Flat | Process weekly, keep it clean |
| `01-Fleeting/` | Nested by date | Daily notes only |
| `02-Literature/` | Shallow nesting | By source type (Books, Articles, etc.) |
| `03-Permanent/` | Flat | Organized by links, not folders |
| `04-MOCs/` | Flat | All MOCs at one level |
| `05-Projects/` | Nested by project | Each project = folder |
| `06-Areas/` | Shallow nesting | By area of responsibility |
| `07-Resources/` | Nested by type | Checklists, guides, snippets |
| `08-Archive/` | Nested by year | Year/month subfolders |
| `09-Meta/` | Flat | System documentation |

## 🔄 Note Progression Workflow

```
Quick Capture → Fleeting Note → Literature Note → Permanent Note → Connected in MOC
```

### 1. Quick Capture
- **Where**: `00-Inbox/` or daily note
- **When**: Immediately when you have an idea
- **Quality**: Rough, just capture

### 2. Fleeting Note
- **Where**: `01-Fleeting/` or daily note
- **When**: Quick thoughts, meeting notes
- **Quality**: For yourself, minimal formatting
- **Lifespan**: Days to weeks

### 3. Literature Note
- **Where**: `02-Literature/`
- **When**: Reading books, articles, courses
- **Quality**: Structured, but in source's words
- **Lifespan**: Permanent, but referenced

### 4. Permanent Note
- **Where**: `03-Permanent/`
- **When**: After processing and reflection
- **Quality**: Refined, in your own words, atomic
- **Lifespan**: Permanent and evergreen
- **Required**: Minimum 1-2 links to other notes

### 5. Connected in MOC
- **Where**: `04-MOCs/`
- **When**: When 10+ notes exist on a topic
- **Quality**: Well-organized, provides navigation
- **Lifespan**: Evolves over time

## 📊 Review Processes

### Daily Review (5 minutes)
- [ ] Review today's daily note
- [ ] Capture any new fleeting thoughts
- [ ] Check active project status

### Weekly Review (30 minutes)
- [ ] Process inbox (move notes to appropriate folders)
- [ ] Transform 2-3 fleeting notes into permanent notes
- [ ] Update active project notes
- [ ] Create/update links between notes

### Monthly Review (60 minutes)
- [ ] Review MOCs for completeness
- [ ] Archive completed projects
- [ ] Check for orphaned notes (no links)
- [ ] Identify emerging topics for new MOCs
- [ ] Update Master Index stats

### Quarterly Review (2 hours)
- [ ] Review system conventions (this document)
- [ ] Assess what's working and what isn't
- [ ] Clean up archive folder
- [ ] Refactor growing MOCs if needed
- [ ] Update system documentation

## ⚠️ Common Pitfalls to Avoid

### Anti-Patterns

❌ **Over-organizing**: Creating folders for everything
- ✅ Instead: Use links and MOCs

❌ **No links**: Permanent notes without connections
- ✅ Instead: Always link to 1-2 related notes

❌ **Letting inbox grow**: 50+ notes in inbox
- ✅ Instead: Process weekly, keep inbox under 20

❌ **Premature MOCs**: Creating MOCs with only 3-4 notes
- ✅ Instead: Wait until you have 10+ related notes

❌ **Copy-paste literature notes**: Copying without processing
- ✅ Instead: Write in your own words in permanent notes

❌ **Perfect naming**: Spending 10 minutes on the perfect title
- ✅ Instead: Use a good-enough title, refactor later if needed

❌ **Tag explosion**: Creating 50+ unique tags
- ✅ Instead: Use links for connections, tags for metadata

## 🎯 Quality Checklist

### For Permanent Notes
- [ ] Has a descriptive, specific title
- [ ] Contains one atomic idea
- [ ] Written in your own words
- [ ] Links to 1-2 related notes minimum
- [ ] Explains context (where the idea came from)
- [ ] Has supporting details or examples
- [ ] Includes questions for future exploration

### For MOCs
- [ ] Name ends with `-MOC`
- [ ] Covers 10+ related notes
- [ ] Has an overview section
- [ ] Organizes notes into logical groups
- [ ] Links to related MOCs
- [ ] Updated when new related notes are created

### For Literature Notes
- [ ] Follows source naming convention
- [ ] Includes bibliographic information
- [ ] Summarizes key takeaways
- [ ] Links to permanent notes created from it
- [ ] Includes personal reflections

## 🔄 Evolution of This System

**This system should evolve with your needs:**

- Start simple, add complexity only when needed
- Review these conventions quarterly
- Adjust rules that aren't serving you
- Document changes so future-you understands why

**Remember**: Conventions exist to serve you, not the other way around. If a rule isn't helping, change it—but change it consciously and document why.

---

**Last Updated**: 2026-04-21
**Next Review**: 2026-07-21
