# Personal Second Brain 🧠

Welcome to my personal knowledge management system—a Zettelkasten-inspired second brain for capturing, organizing, and connecting ideas.

## 🎯 Purpose

This system helps me:
- **Learn & Grow**: Transform fleeting thoughts into permanent knowledge
- **Plan & Execute**: Manage projects and track areas of responsibility
- **Share Knowledge**: Create reference materials and how-to guides
- **Quick Reference**: Access checklists, code snippets, and resources instantly

## 🗺️ Quick Navigation

**Start Here:**
- [[04-MOCs/00-Master-Index|Master Index]] - Central navigation hub
- [[09-Meta/Conventions|System Conventions]] - Naming rules and linking strategy
- [[09-Meta/Review-Process|Review Process]] - Daily, weekly, monthly workflows

**Core Areas:**
- [[00-Inbox/README|Inbox]] - Capture zone for new ideas
- [[03-Permanent/README|Permanent Notes]] - Atomic knowledge notes
- [[04-MOCs/README|Maps of Content]] - Index notes for navigation
- [[05-Projects/README|Projects]] - Active project tracking
- [[07-Resources/README|Resources]] - Reference materials

## 🔄 Core Workflows

### 1. Capture Workflow

**Quick captures:**
```
New idea → 00-Inbox/ (or daily note)
```

**Weekly processing:**
1. Review inbox notes
2. Categorize: Is it fleeting, literature, permanent, or project-related?
3. Move to appropriate folder
4. Create links to related notes
5. Delete what's no longer relevant

### 2. Note Progression

```
Fleeting Note → Literature Note → Permanent Note → Connected in MOC
```

- **Fleeting**: Quick capture, rough thoughts
- **Literature**: Notes from external sources (articles, books, courses)
- **Permanent**: Refined atomic ideas in your own words
- **MOC**: Collections of related permanent notes

### 3. Review Cadence

| Frequency | Focus | Actions |
|-----------|-------|---------|
| **Daily** | Current work | Review daily note, urgent items |
| **Weekly** | Inbox processing | Process inbox, update active projects |
| **Monthly** | System health | Review MOCs, archive completed projects |
| **Quarterly** | System evolution | Conventions review, structure refinement |

## 🚀 Getting Started

### Your First Week

**Day 1:** Create your first note
1. Add a note to `00-Inbox/` about something you learned today
2. Use the permanent note template
3. Don't worry about perfection—just start

**Day 3:** Connect ideas
1. Create a second note
2. Link it to your first note using `[[Note Title]]`
3. Observe how ideas connect

**Day 7:** First review
1. Review your inbox
2. Move notes to `03-Permanent/`
3. Create your first MOC if you have 3+ related notes

### Essential Templates

- `Templates/template-permanent-note.md` - Most frequently used
- `Templates/template-literature-note.md` - For source material
- `Templates/template-moc.md` - For maps of content
- `Templates/template-daily-note.md` - For daily captures
- `Templates/template-project.md` - For project tracking

## 📋 Naming Conventions

- **Permanent Notes**: `YYYYMMDDHHMMSS-descriptive-title.md`
  - Example: `20260421143022-spaced-repetition-learning.md`
- **Literature Notes**: `Author-Year-Title.md` or `Source-YYYY-MM-DD-Title.md`
- **MOCs**: `Topic-Name-MOC.md` (always end with `-MOC`)
- **Projects**: `YYYY-MM-Project-Name/` (date prefix folder)
- **Daily Notes**: `YYYY-MM-DD.md` (in `01-Fleeting/Daily/`)

## 🔗 Linking Strategy

- Use Obsidian wikilinks: `[[Note Title]]`
- Link with aliases: `[[Note Title|Display Text]]`
- **Minimum links**: Every permanent note should link to 1-2 other notes
- **Create MOCs**: When you have 10+ related notes on a topic
- **Prefer links over tags** for connections

## 🏷️ Tag Strategy (Use Sparingly)

- `#status/draft` - Note in progress
- `#status/evergreen` - Refined permanent note
- `#type/literature` - Source material
- `#type/project` - Project-related

## 🎓 Philosophy & Principles

### Core Principles

1. **Atomic Notes**: One idea per note—keeps thinking clear
2. **Progressive Summarization**: From rough captures to refined knowledge
3. **Linking Over Organizing**: Connections matter more than folders
4. **Write for Future You**: Clear titles, explain context
5. **Consistency Over Perfection**: Follow conventions, iterate over time

### The Zettelkasten Method

This system is inspired by Niklas Luhmann's Zettelkasten:
- Notes are atomic (one idea each)
- Notes are connected through links
- Emergence over planning (let structure evolve)
- Knowledge compounds through connections

## 🛠️ Obsidian Setup

### Recommended Settings
- **New file location**: `00-Inbox/`
- **Attachment folder**: `Attachments/`
- **Use wikilinks** (not markdown links)
- **Always update links** when renaming
- **Default view**: Source mode

### Suggested Plugins
**Core:**
- Daily notes
- Templates
- Backlinks
- Graph view

**Community:**
- Templater (advanced templates)
- Calendar (daily note navigation)
- Dataview (query your notes)

## 📊 System Health

### Warning Signs
- Inbox > 20 notes: Time to process!
- No new permanent notes in 2 weeks: Are you capturing?
- MOC has 50+ links: Consider splitting into sub-MOCs
- Projects folder has items > 6 months old: Time to archive

### Best Practices
✅ Start small—inbox, permanent notes, MOCs only at first
✅ Use templates consistently
✅ Link liberally—create connections early
✅ One idea per note
✅ Review regularly
❌ Avoid premature optimization
❌ Don't create empty folders "just in case"
❌ Don't let inbox grow without processing

## 📚 Directory Structure

```
personal_sai_second_brain/
├── 00-Inbox/              # Unsorted captures
├── 01-Fleeting/           # Quick captures & daily notes
├── 02-Literature/         # Source material notes
├── 03-Permanent/          # Main Zettelkasten (atomic notes)
├── 04-MOCs/               # Maps of Content (index notes)
├── 05-Projects/           # Active projects
├── 06-Areas/              # Ongoing responsibilities
├── 07-Resources/          # Reference materials
├── 08-Archive/            # Completed/inactive content
├── 09-Meta/               # System documentation
├── Templates/             # Note templates
└── Attachments/           # Media files
```

## 🆘 Need Help?

- **Conventions unclear?** Check [[09-Meta/Conventions]]
- **Workflow questions?** See [[09-Meta/Review-Process]]
- **Lost in notes?** Start at [[04-MOCs/00-Master-Index]]
- **System not working?** Simplify—return to basics

---

**Last Updated**: 2026-04-21
**Version**: 1.0
**Status**: 🌱 Growing
