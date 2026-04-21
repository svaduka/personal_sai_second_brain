---
title: Maps of Content (MOCs)
type: meta
created: 2026-04-21
---

# 🗺️ Maps of Content (MOCs)

Maps of Content (MOCs) are index notes that organize and provide navigation through related permanent notes on a specific topic.

## Purpose

- **Navigation**: Find related notes easily
- **Organization**: Structure without hierarchical folders
- **Emergence**: See patterns and connections
- **Overview**: Understand a topic at a glance

## What is a MOC?

A MOC is a note that:
- Links to 10+ related permanent notes
- Organizes notes into logical groups
- Provides context about the topic
- Acts as an entry point for exploration
- Always ends with `-MOC` suffix

**Think of MOCs as:**
- A curated library catalog (not a folder)
- A map (not a container)
- A flexible index (not a rigid taxonomy)

## When to Create a MOC

### The 10-Note Rule

Create a MOC when you have **10+ permanent notes** on a related topic.

**Signs you need a MOC:**
- Repeatedly searching for the same group of notes
- Topic keeps coming up in different contexts
- Hard to remember all notes on a subject
- Notes naturally cluster in graph view
- You want to see the "big picture" of a topic

### Don't Create MOCs Too Early

❌ **Premature MOCs** (3-4 notes):
- Creates artificial structure
- Limits organic connections
- Maintenance overhead

✅ **Wait for natural clusters**:
- Let notes accumulate
- Patterns emerge organically
- MOC structure becomes obvious

## MOC Structure

### Standard Template Sections

1. **Overview**: What this MOC covers (2-3 sentences)
2. **Core Concepts**: Foundational ideas (3-7 notes)
3. **Deep Dives**: Organized by subtopic
4. **Practical Applications**: How-tos, checklists
5. **Related MOCs**: Connections to other maps
6. **Key Resources**: Literature notes, external links
7. **Open Questions**: Areas to explore further

### Example Structure

```markdown
# Learning-Methods-MOC

## Overview
Methods and techniques for effective learning...

## Core Concepts
- [[Active-Recall]]
- [[Spaced-Repetition]]
- [[Elaborative-Encoding]]

## Deep Dives

### Memory Techniques
- [[Memory-Palace-Method]]
- [[Chunking-Information]]

### Study Strategies
- [[Pomodoro-Technique]]
- [[Interleaving-Practice]]

## Related MOCs
- [[Productivity-MOC]]
- [[Cognitive-Science-MOC]]
```

## Naming Convention

**Format**: `Topic-Name-MOC.md`

**Always end with `-MOC`**:
- Makes MOCs easily identifiable
- Distinguishes from permanent notes
- Shows up in searches and links

**Examples:**
- ✅ `Learning-Methods-MOC.md`
- ✅ `Distributed-Systems-MOC.md`
- ✅ `Personal-Productivity-MOC.md`
- ❌ `Learning-Index.md` (should use -MOC)
- ❌ `MOC-Learning.md` (wrong order)

## Types of MOCs

### Topic MOCs
Organize notes by subject matter:
- `Machine-Learning-MOC`
- `Writing-Techniques-MOC`
- `Leadership-Principles-MOC`

### Project MOCs
Index project-related knowledge:
- `Website-Redesign-MOC` (links to related permanent notes)
- Not the project folder itself (that's in `05-Projects/`)

### Temporal MOCs
Organize by time period:
- `2026-Q2-Learning-MOC`
- `Career-Transition-2026-MOC`

### Master Index
The MOC of MOCs:
- `00-Master-Index.md` (already exists in this folder)
- Links to all other MOCs
- Primary navigation hub

## Building a Good MOC

### Start Simple

**Initial MOC** (just created):
```markdown
# Topic-MOC

## Core Notes
- [[Note-1]]
- [[Note-2]]
- [[Note-3]]
...
- [[Note-10]]

## Related
- [[Related-MOC]]
```

### Evolve Over Time

**Mature MOC** (15-30 notes):
```markdown
# Topic-MOC

## Overview
[2-3 sentence description]

## Core Concepts
[Foundation notes]

## Subtopic 1
[Related notes grouped]

## Subtopic 2
[More related notes]

## Practical Applications
[How-to guides]

## Related MOCs
[Connections]
```

### Refactor When Needed

**Large MOC** (50+ notes):
- Split into multiple topic-specific MOCs
- Create hierarchy with parent MOC linking to child MOCs
- Keep each MOC focused and navigable

**Example refactoring:**
```
Programming-MOC (60 notes)
└─> Split into:
    ├─ Programming-Languages-MOC
    ├─ Programming-Paradigms-MOC
    ├─ Programming-Tools-MOC
    └─ Programming-MOC (parent, links to others)
```

## MOC vs. Folder

**Folders**:
- Physical containers
- Rigid hierarchy
- Notes can only be in one folder
- Hard to refactor

**MOCs**:
- Virtual indexes
- Flexible connections
- Notes can be in multiple MOCs
- Easy to reorganize

**Use MOCs, not folders** for organizing permanent notes.

## MOC Maintenance

### When Creating New Permanent Notes
- [ ] Check if note belongs in existing MOC
- [ ] Add note to appropriate MOC section
- [ ] Update MOC metadata (note count, last updated)

### During Monthly Review
- [ ] Review each MOC for completeness
- [ ] Add newly created relevant notes
- [ ] Reorganize if sections are unbalanced
- [ ] Check for notes that should be in MOC but aren't
- [ ] Consider splitting if MOC exceeds 50 notes

### MOC Health Indicators

| Status | Note Count | Action |
|--------|------------|--------|
| 🟢 Healthy | 10-30 notes | Maintain structure |
| 🟡 Growing | 31-50 notes | Monitor, may need reorganization |
| 🔴 Large | 51+ notes | Consider splitting into sub-MOCs |

## Linking Strategy

### From MOCs to Notes
```markdown
## Core Concepts
- [[Note-Title]] - Brief description of what this adds
```

### From Notes to MOCs
```markdown
## Connections
Part of: [[Topic-MOC]]
```

### Between MOCs
```markdown
## Related MOCs
- [[Related-MOC]] - How they connect
```

## MOC Patterns

### Hub MOC
Central topic with many connections:
```markdown
# Productivity-MOC
Links to: 45 notes
Connected to: 3 other MOCs
Status: 🌳 Mature
```

### Bridge MOC
Connects two domains:
```markdown
# Code-Review-Best-Practices-MOC
Bridges: [[Software-Engineering-MOC]] & [[Communication-MOC]]
```

### Temporal MOC
Time-bounded collection:
```markdown
# 2026-Learning-Journey-MOC
Period: Jan-Jun 2026
Status: Active
```

## Examples

### Simple MOC (15 notes)
```markdown
---
title: Learning Methods MOC
type: moc
created: 2026-04-21
---

# Learning Methods MOC

## Overview
Effective techniques for learning and retention.

## Core Concepts
- [[Active-Recall]] - Testing strengthens memory
- [[Spaced-Repetition]] - Timed reviews improve retention
- [[Elaborative-Encoding]] - Connect new to existing knowledge

## Memory Techniques
- [[Memory-Palace-Method]]
- [[Chunking-Information]]
- [[Mnemonic-Devices]]

## Study Strategies
- [[Pomodoro-Technique]]
- [[Interleaving-Practice]]
- [[Retrieval-Practice]]

## Related MOCs
- [[Productivity-MOC]]
- [[Note-Taking-MOC]]

## Open Questions
- What's the optimal spacing for different types of knowledge?
- How do learning styles affect technique effectiveness?
```

## Common Mistakes

❌ **Creating MOCs too early**
- ✅ Wait for 10+ related notes

❌ **Making MOCs hierarchical**
- ✅ Keep them flat and cross-linked

❌ **Treating MOCs as containers**
- ✅ Think of them as flexible indexes

❌ **Never updating MOCs**
- ✅ Add new notes during monthly review

❌ **MOCs with no descriptions**
- ✅ Add context for each link

❌ **Copying folder structures**
- ✅ Let MOCs emerge from actual connections

## MOC Workflow

### Creating a MOC

1. **Identify cluster**: Notice 10+ related notes
2. **Use template**: Start with MOC template
3. **Add overview**: Describe the topic scope
4. **Group notes**: Organize into logical sections
5. **Add context**: Brief description for each link
6. **Connect**: Link to related MOCs
7. **Update Master Index**: Add to `00-Master-Index.md`

### Using a MOC

1. **Entry point**: Start here when exploring a topic
2. **Navigation**: Jump to specific notes
3. **Overview**: Understand topic landscape
4. **Discovery**: Find related notes you forgot about

### Maintaining a MOC

1. **Add notes**: When creating permanent notes
2. **Reorganize**: When sections get unbalanced
3. **Split**: When exceeding 50 notes
4. **Update**: During monthly review

---

**Remember**: MOCs are living documents. They should evolve as your knowledge grows. Start simple, add structure when needed, and don't over-engineer early.

**Quick Start**: Begin with `00-Master-Index.md` and create your first topic MOC when you notice 10+ related permanent notes naturally clustering together.
