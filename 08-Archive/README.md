---
title: Archive
type: meta
created: 2026-04-21
---

# 📦 Archive

The archive stores completed projects, outdated notes, and historical content that you want to preserve but don't need in active circulation.

## Purpose

- **Preserve history**: Keep completed work for reference
- **Reduce clutter**: Move inactive content out of active folders
- **Enable retrieval**: Find old projects or ideas if needed
- **Learn from past**: Review past work for insights

## What Goes in Archive

✅ **Archive these:**
- **Completed projects**: Finished projects with final outcomes
- **Cancelled projects**: Projects you're no longer pursuing
- **Old daily notes**: Daily notes older than 3-6 months
- **Inactive areas**: Areas you're no longer maintaining
- **Outdated resources**: Guides that are no longer relevant
- **Superseded notes**: Drafts replaced by better permanent notes
- **Old fleeting notes**: Processed fleeting notes no longer needed

❌ **Don't archive these:**
- **Permanent notes**: Keep these active (they're evergreen)
- **Active MOCs**: Maps of content are navigational, keep accessible
- **Current templates**: Templates should stay in Templates folder
- **Active literature notes**: Keep until fully processed
- **System documentation**: Keep Meta folder active

## Archive Structure

### Recommended Organization

```
08-Archive/
├── 2026/
│   ├── 01-January/
│   │   ├── Projects/
│   │   ├── Daily-Notes/
│   │   └── Other/
│   ├── 02-February/
│   └── 03-March/
├── 2025/
│   ├── Q4/
│   └── ...
└── README.md
```

**Organize by time** (year/month or year/quarter) to:
- Find items chronologically
- Batch delete old archives if needed
- Track project completion timing

### Alternative: By Type

```
08-Archive/
├── Projects/
│   ├── 2026/
│   └── 2025/
├── Daily-Notes/
│   ├── 2026-Q1/
│   └── 2025-Q4/
└── Areas/
    └── 2025/
```

Choose the organization that makes sense for your workflow.

## When to Archive

### During Project Completion

**Immediately after finishing a project:**
1. Document final outcomes
2. Extract learnings to permanent notes
3. Update success criteria
4. Set status to "Completed" or "Cancelled"
5. Move entire project folder to archive

**Archive path:**
```
05-Projects/2026-04-Website-Redesign/
→ 08-Archive/2026/04-April/Projects/2026-04-Website-Redesign/
```

### During Monthly Review

**Archive these monthly:**
- **Completed projects** from last month
- **Daily notes** older than 3 months (or 6 months if you prefer)
- **Inactive projects** with no updates in 2+ months (after confirming they're truly inactive)
- **Old fleeting notes** that have been processed

### During Quarterly Review

**Archive these quarterly:**
- **Areas no longer maintained**: Life circumstances change
- **Outdated resources**: Guides superseded by better versions
- **Old meeting notes**: If not linked to active projects
- **Literature notes**: Fully processed sources you won't reference again

## Archive Workflow

### Archiving a Project

**Step 1: Finalize the project**
```markdown
# 05-Projects/2026-04-Website-Redesign/Project.md

Status: 🔵 Completed
Completed: 2026-04-20

## Final Outcomes
- [Document what was accomplished]

## Learnings Extracted
- [[Permanent-Note-1]] created
- [[Permanent-Note-2]] created
```

**Step 2: Create archive location**
```bash
08-Archive/2026/04-April/Projects/
```

**Step 3: Move project folder**
```
05-Projects/2026-04-Website-Redesign/
→ 08-Archive/2026/04-April/Projects/2026-04-Website-Redesign/
```

**Step 4: Update links**
- Update any permanent notes that reference the project
- Update project-related MOCs
- Update Master Index (remove from active projects)

### Archiving Daily Notes

**Batch archive old daily notes:**

```bash
# Move all daily notes from Q1 2026
01-Fleeting/Daily/2026-01-*.md through 2026-03-*.md
→ 08-Archive/2026/Q1-Daily-Notes/
```

**Before archiving:**
- Review for any valuable insights not yet extracted
- Create permanent notes from unprocessed ideas
- Ensure anything worth keeping is in permanent notes

### Archiving Outdated Resources

**When a resource is superseded:**
1. Create updated version
2. Add note to old version: `⚠️ Outdated - See [[New-Version]]`
3. Move old version to archive
4. Update any links to point to new version

## Accessing Archived Content

### Finding Archived Items

**By date**: If you remember when something was archived
```
08-Archive/2026/03-March/Projects/
```

**By search**: Use Obsidian search
```
path:08-Archive/ [search term]
```

**By links**: If permanent notes link to archived projects
```markdown
Source: [[08-Archive/2026/04-April/Projects/2026-04-Website-Redesign/Project]]
```

### Unarchiving

**To reactivate an archived item:**
1. Move back to appropriate active folder
2. Update status (from "Completed" to "Active")
3. Add to Master Index if needed
4. Resume work

**Common scenario:**
- Restarting a cancelled project
- Revisiting an old area of responsibility
- Using archived project as template

## Archive Maintenance

### During Quarterly Review

**Archive health check:**
- [ ] Verify archives are organized consistently
- [ ] Check that recent projects were archived
- [ ] Remove true clutter if any (notes with no value)
- [ ] Consider permanently deleting archives older than 3-5 years (if desired)

### Long-Term Archive Strategy

**Keep indefinitely:**
- Completed projects (valuable reference)
- Historical daily notes (time capsule)
- Learnings and outcomes

**Can delete after 3-5 years:**
- Routine daily notes with no insights
- Cancelled projects that went nowhere
- Outdated resources with no historical value
- Meeting notes with no lasting relevance

**Deletion vs. Archive:**
- Archive: Might have future reference value
- Delete: No conceivable future use

*When in doubt, archive—storage is cheap.*

## Archive Conventions

### Naming Archived Folders

**Keep original names** when archiving:
```
2026-04-Website-Redesign  ← Keep this exact name
```

**Don't rename** with "archived-" prefix or similar—the location in `08-Archive/` makes it clear.

### Status Indicators

**In project notes, mark status clearly:**
```markdown
---
status: Completed
archived: 2026-04-20
archived-location: 08-Archive/2026/04-April/Projects/
---
```

### Linking to Archived Content

**Use full path in links:**
```markdown
Source: [[08-Archive/2026/04/Projects/2026-04-Website-Redesign/Project]]
```

**Or use aliases:**
```markdown
Source: [[08-Archive/2026/04/Projects/2026-04-Website-Redesign/Project|Website Redesign Project]]
```

## Common Mistakes

❌ **Never archiving**
- Active folders become cluttered
- ✅ Archive completed projects within a week

❌ **Archiving too soon**
- Moving active projects prematurely
- ✅ Only archive when truly complete or inactive 2+ months

❌ **Archiving permanent notes**
- Permanent notes should stay active
- ✅ Only archive drafts superseded by better notes

❌ **Deleting instead of archiving**
- Losing valuable historical reference
- ✅ Archive first, delete later if truly unnecessary

❌ **Messy archive structure**
- Can't find anything
- ✅ Use consistent year/month organization

❌ **No extraction before archiving**
- Losing valuable insights
- ✅ Always extract learnings to permanent notes first

## Archive Decision Tree

```
Is this content still active?
├─ Yes → Keep in active folders
└─ No → Is it valuable for reference?
    ├─ Yes → Archive
    └─ No → Delete (or archive if unsure)
```

**When archiving projects:**
```
Is project complete?
├─ Yes → Extract learnings?
│   ├─ Yes → Create permanent notes
│   └─ Done
└─ Then archive

Is project inactive 2+ months?
├─ Yes → Will you resume?
│   ├─ Maybe → Mark "On Hold", archive
│   └─ No → Mark "Cancelled", archive
└─ Keep active
```

## Archive Benefits

### Cleaner Active Workspace
- Only current work visible
- Easier to find active items
- Reduced cognitive load

### Historical Reference
- Review past projects for insights
- Reference completed work
- Learn from successes and failures

### Perspective Over Time
- See growth and evolution
- Appreciate completed work
- Identify patterns in interests

### Optional Nostalgia
- Old daily notes are time capsules
- Completed projects show accomplishments
- Track journey over years

## Quick Archive Checklist

**Before archiving a project:**
- [ ] Mark status as Completed/Cancelled
- [ ] Add completion date
- [ ] Extract key learnings to permanent notes
- [ ] Update any MOCs that referenced this project
- [ ] Move to appropriate archive folder (YYYY/MM/)
- [ ] Update Master Index (remove from active)

**Before archiving daily notes:**
- [ ] Review for valuable insights
- [ ] Create permanent notes from unprocessed ideas
- [ ] Batch move to archive by time period

**Before archiving resources:**
- [ ] Verify resource is truly outdated
- [ ] Create updated version if needed
- [ ] Update links to point to new version

---

**Remember**: The archive is not a junk drawer—it's a curated historical record. Archive thoughtfully, organize consistently, and trust that completed work is just as valuable archived as it was active. The goal is not zero archive, but clean active folders and accessible history.
