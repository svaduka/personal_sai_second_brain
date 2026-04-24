---
name: initiate_idea
description: Capture a new idea following Zettelkasten workflow with proper naming, linking, and structure
---

You are helping the user capture a new idea in their Zettelkasten-style second brain system. Follow this process carefully to ensure proper structure, naming, and connections.

## Step 1: Gather Idea Information

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

1. Generate current timestamp in format: `YYYYMMDDHHMMSS`
2. Convert the idea title to kebab-case (lowercase with hyphens)
3. Create filename: `YYYYMMDDHHMMSS-idea-title.md`

**Example:**
- Title: "Spaced Repetition Learning"
- Timestamp: `20260422153045`
- Filename: `20260422153045-spaced-repetition-learning.md`

## Step 5: Create the Note

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

## Step 6: Confirm and Create

1. Show the user a summary:
   - Filename: `YYYYMMDDHHMMSS-title.md`
   - Location: `00-Inbox/` or `03-Permanent/`
   - Connections: [List of linked notes]

2. Ask for confirmation

3. Create the file in the appropriate location

4. Confirm creation and remind them:
   - If placed in **Inbox**: "Process during weekly review to move to permanent notes"
   - If placed in **Permanent**: "Note created with [X] connections. Consider adding to a relevant MOC during monthly review"

## Step 7: Post-Creation Suggestions

After creating the note:
1. If 10+ related notes exist on this topic and no MOC exists, suggest: "You have [X] notes on [topic]. Consider creating a MOC: `[Topic-Name-MOC.md]`"
2. If a relevant MOC exists, suggest: "Consider adding this note to [[Existing-MOC]]"

## Important Rules

- **Always use timestamp prefix**: `YYYYMMDDHHMMSS-title.md` for permanent notes
- **Always search for connections**: Every permanent note needs 1-2 links minimum
- **One atomic idea**: If user describes multiple ideas, suggest creating separate notes
- **User's own words**: Ensure the main idea is in their words, not copy-pasted
- **Kebab-case titles**: lowercase-with-hyphens
- **No special characters** in filenames: avoid `/`, `\`, `:`, `*`, `?`, `"`, `<`, `>`, `|`

## Example Interaction Flow

```
Claude: "Let's capture your idea! What's the core concept you want to note?"
User: "The compound effect of daily learning"
Claude: "Great! Where did this idea come from?"
User: "Reading about learning systems and personal experience"
Claude: "Can you explain the main concept in 2-3 sentences?"
User: [provides explanation]
Claude: "Any supporting details or examples?"
User: [provides details]
Claude: "Let me search for related notes..."
[Shows search results]
Claude: "I found these related notes:
- 20260415120000-spaced-repetition-learning.md
- 20260418093000-knowledge-compounds-over-time.md
- Learning-Methods-MOC.md
Which ones connect to your idea?"
User: [selects connections]
Claude: "Is this a quick capture or a refined idea?"
User: "Refined"
Claude: [Shows summary]
"I'll create: 03-Permanent/20260422153045-compound-effect-daily-learning.md
With connections to 2 notes and 1 MOC. Proceed?"
User: "Yes"
Claude: [Creates note]
"✓ Created permanent note with 3 connections. Consider reviewing during monthly MOC updates."
```

## Quality Checklist

Before creating the note, ensure:
- [ ] Timestamp prefix is correct (YYYYMMDDHHMMSS)
- [ ] Title is descriptive and kebab-case
- [ ] At least 1-2 connections are identified (for permanent notes)
- [ ] Main idea is atomic (single concept)
- [ ] Context explains origin
- [ ] Note is in user's own words

## Output

After successful creation, output:
- ✓ Full file path of created note
- ✓ Number of connections made
- ✓ Suggested next action (weekly review if inbox, MOC update if permanent)
