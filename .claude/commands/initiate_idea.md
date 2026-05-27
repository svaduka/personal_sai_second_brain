---
name: initiate_idea
description: Capture a new idea following Zettelkasten workflow with proper naming, linking, and structure
---

You are helping the user capture a new idea or continue an existing idea in their Zettelkasten-style second brain system. Follow this process carefully to ensure proper structure, naming, linking, updates, and connections.

## Step 0: Check for Existing Ideas in Inbox

Before creating a new idea, scan the `00-Inbox/` folder for existing idea notes.

1. List all Markdown files in `00-Inbox/`
2. Identify notes that appear to be ideas or draft idea captures
3. Present the existing idea notes to the user in a table
4. Ask the user whether they want to:
   - continue/update an existing idea
   - create a new idea

### Output Format

| Option | Existing Idea Note | Created Date / Timestamp | Short Description |
|--------|--------------------|--------------------------|-------------------|
| 1 | `YYYYMMDDHHMMSS-example-idea.md` | YYYY-MM-DD HH:mm:ss | Brief summary if available |
| 2 | `new-idea` | N/A | Create a new idea |

If `00-Inbox/` has no existing idea notes, proceed directly to creating a new idea.

### Existing Idea Selection Rules

- If the user selects an existing idea, read the existing note completely before asking questions
- Summarize what already exists in the note
- Ask the user what they want to add, clarify, or change
- Preserve existing content unless the user explicitly asks to modify it
- Append new information in the proper section where possible
- Update the `modified` timestamp
- Do not create a duplicate idea note for the same idea unless the user explicitly asks for a separate note

## Step 1: Gather or Update Idea Information

If the user selected an existing idea, use these questions to update or refine the existing note instead of creating a new note.

Ask the user these questions to capture the essential details:

1. **What is the core idea?** (This will become the note title - ask for a short, descriptive phrase)
2. **Where did this idea come from?** (Origin: book, article, conversation, observation, personal thought, etc.)
3. **What's the main concept?** (Ask them to explain the idea in 2-3 sentences in their own words)
4. **Any supporting details?** (Examples, evidence, key points that elaborate on the main idea)
5. **What questions remain?** (What's unclear or worth exploring further?)

## Step 2: Determine Refinement Level

Ask the user:
- **Is this a quick capture (rough thought)** → Place in `00-Inbox/`
- **Is this a refined atomic idea** → Place in `03-Permanent/`

If unsure, default to `00-Inbox/` and let weekly review process it.

## Step 3: Search for Related Notes

Before creating the note, search for related existing notes to suggest connections:

1. Extract key concepts/terms from the idea
2. Search `03-Permanent/` for related notes using grep with relevant keywords
3. Also search MOCs in `04-MOCs/` that might be relevant
4. Present 3-5 most relevant notes to the user and ask which ones they want to link to

**Example search commands:**
```bash
# Search for notes containing key concepts
grep -r "keyword" 03-Permanent/ 04-MOCs/ --include="*.md"
```

Present findings and ask: "I found these related notes. Which ones connect to your new idea?"

## Step 4: Generate Timestamp and Filename

If the user selected an existing idea, reuse the existing filename and only update the `modified` timestamp. Do not generate a new filename unless the user explicitly asks to split the idea into a new note.

1. Generate current timestamp in format: `YYYYMMDDHHMMSS`
2. Convert the idea title to kebab-case (lowercase with hyphens)
3. Create filename: `YYYYMMDDHHMMSS-idea-title.md`

**Example:**
- Title: "Spaced Repetition Learning"
- Timestamp: `20260422153045`
- Filename: `20260422153045-spaced-repetition-learning.md`

## Step 5: Create or Update the Note

- For a new idea, create the note using the template below
- For an existing idea, update the existing note while preserving existing useful content
- Append new details to the correct sections when possible
- Add a short update note if the new information changes the meaning or direction of the idea

Create the note with this structure (following the permanent note template):

```markdown
---
title: [User's title]
created: YYYY-MM-DD HH:mm:ss
modified: YYYY-MM-DD HH:mm:ss
tags:
  - status/draft
aliases:
  - [Alternative names if any]
---

# [Title]

## Context

> Where did this idea come from? What prompted you to capture it?

- **Origin**: [From user's answer]
- **Date captured**: [Today's date]
- **Why now**: [Why this is relevant or interesting]

## Main Idea

> The core concept in your own words. One atomic idea.

[User's main concept explanation - 2-3 sentences]

## Supporting Details

> Evidence, examples, or elaboration that develops the main idea

[User's supporting details as bullet points]
-
-

## Connections

> Links to related notes - aim for at least 1-2 connections

[Based on search results and user selections]
- **Related to**: [[Related-Note]]
- **Example of**: [[Broader-Concept]]
- **Part of**: [[Relevant-MOC]]

## Questions

> What remains unclear or worth exploring further?

[User's questions]
-
-

## Sources

> References to literature notes or external sources

[If applicable, add literature note links]
- [[Source-Note]]

---

## Metadata

**Status**: #status/draft
**Type**: [Permanent Note or Inbox Item]
**Review Date**: [Today's date]
```

## Step 6: Confirm and Create or Update

1. Show the user a summary:
   - Mode: `new idea` or `existing idea update`
   - Filename: `YYYYMMDDHHMMSS-title.md` or existing filename
   - Location: `00-Inbox/` or `03-Permanent/`
   - Connections: [List of linked notes]
   - Planned changes: [Summary of additions or updates]

2. Ask for confirmation

3. Create or update the file in the appropriate location

4. Confirm completion and remind them:
   - If placed in **Inbox**: "Process during weekly review to move to permanent notes"
   - If placed in **Permanent**: "Note created or updated with [X] connections. Consider adding to a relevant MOC during monthly review"

## Step 7: Post-Creation Suggestions

After creating the note:
1. If 10+ related notes exist on this topic and no MOC exists, suggest: "You have [X] notes on [topic]. Consider creating a MOC: `[Topic-Name-MOC.md]`"
2. If a relevant MOC exists, suggest: "Consider adding this note to [[Existing-MOC]]"

## Important Rules

- **Always use timestamp prefix**: `YYYYMMDDHHMMSS-title.md` for permanent notes
- **Check Inbox first**: Always scan `00-Inbox/` for existing ideas before creating a new idea
- **Always search for connections**: Every permanent note needs 1-2 links minimum
- **One atomic idea**: If user describes multiple ideas, suggest creating separate notes
- **User's own words**: Ensure the main idea is in their words, not copy-pasted
- **Kebab-case titles**: lowercase-with-hyphens
- **No special characters** in filenames: avoid `/`, `\`, `:`, `*`, `?`, `"`, `<`, `>`, `|`
- **Avoid duplicates**: If a similar idea already exists in `00-Inbox/`, ask whether to update it instead of creating a new note

## Quality Checklist

Before creating the note, ensure:
- [ ] `00-Inbox/` was scanned for existing ideas
- [ ] Timestamp prefix is correct (YYYYMMDDHHMMSS)
- [ ] Title is descriptive and kebab-case
- [ ] At least 1-2 connections are identified (for permanent notes)
- [ ] Main idea is atomic (single concept)
- [ ] Context explains origin
- [ ] Note is in user's own words

## Output

After successful creation or update, output:
- ✓ Full file path of created or updated note
- ✓ Number of connections made
- ✓ Suggested next action (weekly review if inbox, MOC update if permanent)
