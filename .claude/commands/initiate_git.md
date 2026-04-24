---
name: initiate_git
description: Sync second brain with git - pull remote changes, analyze local changes, create structured commit message, and push
---

You are helping the user sync their second brain repository with git. Follow this comprehensive workflow to ensure safe synchronization with meaningful commit messages.

## Step 1: Pre-Sync Status Check

First, check the current git status to understand the starting state:

```bash
git status
```

Show the user:
- Current branch (should be `main`)
- Number of modified files
- Number of untracked files
- Any uncommitted changes

**Safety check**: If not on `main` branch, warn the user and ask if they want to switch to main or proceed on current branch.

## Step 2: Pull Remote Changes

Pull the latest changes from the remote repository:

```bash
git pull origin main
```

**Handle outcomes**:
- ✅ **Already up to date**: Proceed to check local changes
- ✅ **Fast-forward merge**: Show what was pulled and proceed
- ⚠️ **Merge conflicts**: Stop and inform the user. Ask if they want help resolving conflicts.
- ❌ **Error (no remote, network issue)**: Report error and ask if they want to proceed with local commit only

## Step 3: Analyze Local Changes

Run these commands to categorize all changes:

```bash
# Get staged and unstaged changes
git status --porcelain

# Show detailed diff for context
git diff --stat
```

Categorize the changes by directory/type:

### Change Categories

Analyze and group files by location:

**Knowledge Notes:**
- `00-Inbox/` - New captures
- `01-Fleeting/` - Daily notes
- `02-Literature/` - Literature notes
- `03-Permanent/` - Permanent notes (core knowledge)
- `04-MOCs/` - Maps of Content

**Organization:**
- `05-Projects/` - Project files
- `06-Areas/` - Areas of responsibility
- `07-Resources/` - Resources
- `08-Archive/` - Archived items

**System:**
- `09-Meta/` - System documentation
- `Templates/` - Templates
- `.claude/` - Claude commands
- Root files - `README.md`, `CLAUDE.md`, etc.

Count files in each category:
- Added (new files): `A` in git status
- Modified (changed files): `M` in git status
- Deleted (removed files): `D` in git status
- Renamed (moved files): `R` in git status

## Step 4: Generate Structured Commit Message

Create a commit message that lists changes by category:

### Commit Message Format

```
[Type] Brief summary of changes

Knowledge Updates:
- Added X permanent note(s)
- Modified X note(s)
- Processed inbox items

Organizational Changes:
- Updated X project(s)
- Modified X resource(s)

System Updates:
- Updated system documentation
- Modified templates/commands

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>
```

### Determine Commit Type Prefix

Based on what changed, use one of these prefixes:

- `[Notes]` - Added/modified permanent or literature notes
- `[Capture]` - Added to inbox or fleeting notes
- `[MOC]` - Created/updated Maps of Content
- `[Project]` - Project-related updates
- `[System]` - Templates, meta, or system files
- `[Review]` - Weekly/monthly review processing
- `[Archive]` - Archived items
- `[Sync]` - General sync with mixed changes

### Example Commit Messages

**Example 1: New permanent notes**
```
[Notes] Add 3 permanent notes on distributed systems

Knowledge Updates:
- Added: 03-Permanent/20260422153045-eventual-consistency.md
- Added: 03-Permanent/20260422154120-cap-theorem.md
- Added: 03-Permanent/20260422155230-consensus-algorithms.md
- Modified: 04-MOCs/Distributed-Systems-MOC.md (added new notes)

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>
```

**Example 2: Weekly review**
```
[Review] Weekly review - processed inbox and updated projects

Knowledge Updates:
- Added 2 permanent notes from inbox processing
- Processed 8 inbox items

Organizational Changes:
- Updated 2 active projects
- Archived 1 completed project

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>
```

**Example 3: System updates**
```
[System] Update templates and commands

System Updates:
- Modified: Templates/template-permanent-note.md
- Added: .claude/commands/initiate_idea.md
- Updated: CLAUDE.md

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>
```

## Step 5: Show Commit Preview

Before committing, show the user:

1. **Summary statistics**:
   ```
   Changes to commit:
   - 5 files added
   - 3 files modified
   - 1 file deleted

   By category:
   - Permanent notes: 3 added, 1 modified
   - MOCs: 1 modified
   - Projects: 1 modified
   ```

2. **Generated commit message** (show the full message)

3. **File list** (organized by category):
   ```
   Knowledge Notes:
     A  03-Permanent/20260422153045-eventual-consistency.md
     M  04-MOCs/Distributed-Systems-MOC.md

   Projects:
     M  05-Projects/2026-04-Learning-Systems/progress.md
   ```

4. Ask for confirmation: "Proceed with this commit and push to main?"

## Step 6: Stage All Changes

Stage all changes for commit:

```bash
git add -A
```

**Important**: Show the user what will be staged. Warn if:
- `.env` files or credentials detected
- Large binary files detected (> 10MB)
- Unexpected file types detected (e.g., `.exe`, `.zip`)

## Step 7: Create Commit

Commit with the generated message:

```bash
git commit -m "$(cat <<'EOF'
[Generated commit message here]
EOF
)"
```

**Verify commit**:
```bash
git log -1 --oneline
```

Show the commit hash and first line to confirm success.

## Step 8: Push to Remote

Push the commit to the main branch:

```bash
git push origin main
```

**Handle outcomes**:
- ✅ **Success**: Confirm push and show summary
- ⚠️ **Rejected (non-fast-forward)**: Someone else pushed. Suggest pulling again and retrying
- ❌ **No remote / Network error**: Inform user that commit is local only

## Step 9: Post-Sync Summary

Show final status:

```
✓ Sync complete!

Summary:
- Pulled: [X changes from remote / Already up to date]
- Committed: [X files] with message "[commit title]"
- Pushed: Successfully to origin/main

Local repository is now in sync with remote.

Next suggested action:
[Based on what was committed, suggest next action]
```

### Suggested Next Actions

Based on what was committed, suggest:

- **If inbox items added**: "Run weekly review to process inbox items"
- **If many permanent notes added**: "Consider creating/updating relevant MOCs"
- **If 10+ notes on a topic**: "Consider creating a new MOC for [topic]"
- **If changes to templates**: "Review existing notes for consistency"

## Error Handling

### Merge Conflicts

If merge conflicts occur during pull:

1. Show conflict files:
   ```bash
   git diff --name-only --diff-filter=U
   ```

2. For each conflict file, show:
   ```bash
   git diff [file]
   ```

3. Ask user: "Would you like me to help resolve these conflicts?"

4. If yes, guide through conflict resolution for each file

### Uncommitted Changes During Pull

If pull fails due to uncommitted changes:

1. Inform user: "You have local changes that would be overwritten by pull"
2. Options:
   - **Stash and pull**: `git stash && git pull && git stash pop`
   - **Commit first then pull**: Proceed with commit workflow first
   - **Abort**: Stop the sync

### No Remote Repository

If no remote is configured:

1. Inform user: "No remote repository configured"
2. Ask: "Would you like to:"
   - Add a remote repository
   - Continue with local commits only
   - Abort the sync

## Important Safety Rules

### Pre-Commit Checks

Before committing, verify:
- [ ] No sensitive files (`.env`, `credentials`, `secrets`)
- [ ] No large binary files (> 10MB) unless intentional
- [ ] No files outside expected directories
- [ ] Commit message is meaningful and structured

### Branch Protection

- Always confirm branch before pushing
- Warn if pushing to `main` with force flags
- Never use `git push --force` without explicit user confirmation

### Commit Message Quality

Ensure commit messages:
- [ ] Start with a type prefix: `[Notes]`, `[Review]`, `[System]`, etc.
- [ ] Have a clear summary line (< 72 characters)
- [ ] List specific changes by category
- [ ] Include Co-Authored-By line for Claude

### User Confirmation Points

Ask for confirmation before:
1. Switching branches
2. Staging files (show what will be staged first)
3. Committing (show message preview)
4. Pushing to remote
5. Any destructive operations (force push, reset, etc.)

## Quick Mode (Optional)

If user wants a quick sync without interaction, support a "quick mode":

```
/initiate_git --quick
```

In quick mode:
- Auto-generate commit message
- Auto-confirm if no conflicts or issues
- Only stop for conflicts or errors
- Still show summary at the end

## Usage Examples

### Example 1: First time sync after adding notes

```
You: /initiate_git
Claude: Checking git status...
Current branch: main
Found 3 modified files, 2 new files

Pulling from origin/main...
Already up to date.

Analyzing changes...
Knowledge Notes:
- Added: 03-Permanent/20260422153045-idea.md
- Added: 03-Permanent/20260422154120-another-idea.md
- Modified: 04-MOCs/00-Master-Index.md

Generated commit message:
[Notes] Add 2 permanent notes on learning

Knowledge Updates:
- Added 2 permanent notes
- Modified Master Index MOC

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>

Proceed with commit and push? [y/n]
You: y
Claude: Staging changes...
Committing...
✓ Committed: a1b2c3d [Notes] Add 2 permanent notes
Pushing to origin/main...
✓ Push successful!

Sync complete! 2 files committed and pushed.
```

### Example 2: Sync with remote changes

```
You: /initiate_git
Claude: Pulling from origin/main...
✓ Pulled 1 commit with 2 file changes
  - Modified: README.md
  - Added: 09-Meta/New-Convention.md

Analyzing local changes...
[continues workflow...]
```

## Implementation Notes

- Use `git status --porcelain` for machine-readable status
- Use `git log -1 --format=%H` to get commit hash
- Use heredoc for multi-line commit messages to preserve formatting
- Always show user what will happen before destructive operations
- Group similar files together in commit messages
- Limit file lists in commit message to ~10 files max, summarize if more

## Output Format

Maintain consistent output with:
- ✓ Success indicators (green checkmark)
- ⚠️ Warning indicators (yellow warning)
- ❌ Error indicators (red X)
- Clear section headers
- Indented lists for file changes
- Summary statistics at key points
