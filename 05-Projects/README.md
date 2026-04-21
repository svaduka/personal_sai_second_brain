---
title: Projects
type: meta
created: 2026-04-21
---

# 🎯 Projects

Projects are temporal, goal-oriented work with defined outcomes and timelines. They have a clear beginning, middle, and end.

## Purpose

- **Track active work**: Document project progress
- **Maintain context**: Keep project-related information together
- **Log decisions**: Record why choices were made
- **Enable handoffs**: Others (or future you) can understand project state
- **Extract learnings**: Transform project insights into permanent notes

## What is a Project?

**Projects have:**
- ✅ Clear goal and success criteria
- ✅ Defined timeline (start and target completion)
- ✅ Specific deliverables
- ✅ Temporal nature (they end)
- ✅ Action-oriented tasks

**Projects are NOT:**
- ❌ Ongoing responsibilities (use `06-Areas/` instead)
- ❌ General knowledge (use `03-Permanent/` instead)
- ❌ Quick tasks (use daily notes or task manager)
- ❌ Reference material (use `07-Resources/` instead)

## Project vs. Area

| Aspect | Project | Area |
|--------|---------|------|
| **Timeline** | Has end date | Ongoing |
| **Goal** | Specific outcome | Maintain standard |
| **Examples** | "Launch new website" | "Health & fitness" |
| **Status** | Active/Complete | Always active |
| **Location** | `05-Projects/` | `06-Areas/` |

**Rule of thumb**: If it can be "completed" → Project. If it requires continuous attention → Area.

## Naming Convention

**Format**: `YYYY-MM-Project-Name/` (folder)

**Examples:**
- ✅ `2026-04-Website-Redesign/`
- ✅ `2026-03-Learn-Rust/`
- ✅ `2026-04-Home-Office-Setup/`
- ❌ `website-project/` (missing date prefix)
- ❌ `2026-Project/` (too vague)

**Why date prefix?**
- Chronological sorting
- Easy to see when project started
- Helps identify stale projects during review

## Project Structure

### Folder Organization

**Each project gets its own folder:**
```
05-Projects/
├── 2026-04-Website-Redesign/
│   ├── Project.md              # Main project note
│   ├── research.md             # Research notes
│   ├── decisions.md            # Key decisions
│   ├── meeting-notes.md        # Meeting logs
│   └── resources/              # Project-specific files
├── 2026-03-Learn-Rust/
│   └── Project.md
└── 2026-04-Write-Blog-Series/
    └── Project.md
```

**Minimum**: Each project folder has `Project.md` using project template

## Project Lifecycle

### 1. Initiation
```markdown
Status: 🟢 Active
Phase: Planning
```
- Create project folder with date prefix
- Fill out project template
- Define goal and success criteria
- Set timeline
- List next actions

### 2. Execution
```markdown
Status: 🟢 Active
Phase: In Progress
```
- Weekly progress updates
- Log decisions and blockers
- Update next actions
- Link to related permanent notes
- Track time and resources

### 3. Completion
```markdown
Status: 🔵 Completed
Phase: Done
```
- Document final outcomes
- Extract learnings to permanent notes
- Update success criteria checkboxes
- Archive project folder

### 4. Archival
```markdown
Status: 🔵 Archived
Location: 08-Archive/2026/04/
```
- Move to `08-Archive/YYYY/MM/`
- Keep project notes for future reference
- Link from permanent notes to archived project

## Project Template Sections

### Essential Sections
1. **Goal & Success Criteria**: What defines done?
2. **Timeline**: Start, target, and actual completion dates
3. **Next Actions**: What needs to happen next?
4. **Progress Log**: Regular updates on what's happening
5. **Connected Notes**: Links to permanent notes and MOCs

### Optional Sections
- **Context**: Background and motivation
- **Key Resources**: People, tools, documents
- **Project Plan**: Phases and milestones
- **Decisions & Trade-offs**: What was chosen and why
- **Blockers & Risks**: What's preventing progress
- **Notes & Learnings**: Insights gained

## Project Workflows

### Daily Project Work

**Morning:**
1. Review project note
2. Check next actions
3. Start with highest priority

**Throughout day:**
1. Work on project tasks
2. Note decisions as you make them
3. Update blockers if encountered

**End of day:**
1. Quick progress log entry
2. Update next actions for tomorrow
3. Note any new insights

### Weekly Project Review

**For each active project:**
- [ ] Add weekly progress log entry
- [ ] Update next actions list
- [ ] Review and adjust timeline if needed
- [ ] Document any key decisions made
- [ ] Note any blockers encountered
- [ ] Link to any new permanent notes created

### Monthly Project Review

**For all projects:**
- [ ] Archive completed projects (move to `08-Archive/`)
- [ ] Review projects inactive for 2+ months
  - Either: Resume, Close, or Archive
- [ ] Extract learnings from completed projects to permanent notes
- [ ] Update project-related MOCs

## Connecting Projects to Knowledge

### During the Project

**Link from project to permanent notes:**
```markdown
## Connected Notes
- [[Permanent-Note]] - Relevant concept
- [[MOC-Name]] - Related topic area
```

**Reference in daily work:**
- Project decisions informed by permanent notes
- Apply concepts from knowledge base

### After the Project

**Extract learnings to permanent notes:**

From project:
```markdown
# 2026-04-Website-Redesign/Project.md

## Learnings
- Mobile-first design led to better UX
- User testing caught 80% of issues
- Stakeholder alignment crucial upfront
```

To permanent notes:
```markdown
# 20260421163000-mobile-first-design-benefits

Mobile-first design forces focus on essential features...

Source: [[2026-04-Website-Redesign/Project]]
```

## Project Status Indicators

### Status Codes

- 🟢 **Active**: Currently working on it
- 🟡 **On Hold**: Paused but plan to resume
- 🔵 **Completed**: Successfully finished
- 🔴 **Cancelled**: No longer pursuing
- ⚪ **Someday/Maybe**: Not committed yet

### Priority Levels

- **High**: Must finish soon, high impact
- **Medium**: Important but not urgent
- **Low**: Nice to have, low urgency

## Types of Projects

### Learning Projects
```markdown
# 2026-03-Learn-Rust/Project.md

Goal: Build proficiency in Rust programming
Timeline: 3 months
Success: Complete 3 real projects in Rust
```

### Creative Projects
```markdown
# 2026-04-Write-Blog-Series/Project.md

Goal: Publish 10-part series on second brains
Timeline: 2 months
Success: All posts published and shared
```

### Life Projects
```markdown
# 2026-04-Home-Office-Setup/Project.md

Goal: Create productive home office space
Timeline: 1 month
Success: Ergonomic setup, good lighting, organized
```

### Work Projects
```markdown
# 2026-04-API-Redesign/Project.md

Goal: Refactor API for better performance
Timeline: 6 weeks
Success: 50% latency reduction, backward compatible
```

## Common Mistakes

❌ **Projects without clear success criteria**
- ✅ Define what "done" looks like upfront

❌ **Never updating project notes**
- ✅ Weekly progress logs keep context alive

❌ **Treating ongoing work as projects**
- ✅ Use Areas for continuous responsibilities

❌ **Letting completed projects linger**
- ✅ Archive within a week of completion

❌ **No extraction of learnings**
- ✅ Always create permanent notes from project insights

❌ **Too many active projects**
- ✅ Limit to 3-5 active projects maximum

## Project Organization Tips

### Limit Active Projects

**Recommended: 3-5 active projects maximum**

More than 5 active projects → spread too thin

**If overwhelmed:**
1. Mark some projects "On Hold"
2. Focus on 1-2 highest priority
3. Complete before starting new ones

### Project Stacking

**Sequential** (one after another):
- Finish project A completely
- Then start project B
- Better focus and completion rate

**Parallel** (multiple at once):
- Useful if projects have different contexts
- Example: One work project + one learning project
- Max 3-4 parallel projects

### Project Templates

Create project-specific templates if you do similar projects repeatedly:
```
Templates/
├── template-project.md        # General project
├── template-learning-project.md
├── template-writing-project.md
└── template-client-project.md
```

## Quick Start Checklist

**Starting a new project:**
- [ ] Create project folder with date prefix
- [ ] Use project template for `Project.md`
- [ ] Define clear goal and success criteria
- [ ] Set start and target completion dates
- [ ] List 3-5 next actions
- [ ] Link to relevant permanent notes or MOCs
- [ ] Add to Master Index or weekly review list

**Completing a project:**
- [ ] Mark all success criteria as complete (or document why not)
- [ ] Add final completion date
- [ ] Write project retrospective in learnings section
- [ ] Extract key insights to permanent notes
- [ ] Update any relevant MOCs
- [ ] Move folder to `08-Archive/YYYY/MM/`

---

**Remember**: Projects are vehicles for creating value and learning. Document as you go, extract learnings when done, and let completed projects inform future permanent notes. The goal isn't just to complete projects—it's to grow your knowledge base through the work you do.
