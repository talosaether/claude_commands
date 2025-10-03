You are implementing a workspace cleanup workflow. This command resets the current working session by removing untracked artifacts and reverting uncommitted changes to prepare for the next task.

## Workflow Overview

This workflow helps maintain a clean workspace by:
- Removing untracked files and artifacts
- Reverting uncommitted changes
- Restoring the workspace to a clean git state
- Optionally stashing work in progress for later retrieval

## Phase 1: Assessment

Before cleaning, understand what will be affected:

1. **Check Current Status**
   ```bash
   git status
   ```
   - See all untracked files
   - See all uncommitted changes
   - Identify what will be removed/reverted

2. **Ask User for Confirmation**
   Present the list of files that will be affected and ask:
   - "I found X untracked files and Y modified files. Clean all? Or selective cleanup?"
   - Options:
     - **Clean all** - Remove all untracked, revert all changes
     - **Selective** - User chooses what to keep
     - **Stash** - Save work in progress for later
     - **Cancel** - Abort cleanup

## Phase 2: Cleanup Strategy

Based on user preference, execute the appropriate cleanup:

### Option A: Clean All (Fresh Start)

1. **Remove All Untracked Files**
   ```bash
   git clean -fd
   ```
   - `-f` = force removal
   - `-d` = remove untracked directories too
   - Removes ALL untracked files and directories

2. **Revert All Uncommitted Changes**
   ```bash
   git restore .
   ```
   - Reverts all modified tracked files
   - Returns workspace to last commit state

3. **Unstage Everything**
   ```bash
   git restore --staged .
   ```
   - Unstages any staged changes
   - Useful if files were added but not committed

### Option B: Selective Cleanup

1. **Show Interactive List**
   ```bash
   # List untracked files
   git ls-files --others --exclude-standard

   # List modified files
   git diff --name-only
   ```

2. **Remove Specific Untracked Files**
   ```bash
   rm file1.txt file2.txt
   rm -rf directory/
   ```
   - User specifies which files to remove
   - Keep important work in progress

3. **Revert Specific Files**
   ```bash
   git restore file1.js file2.js
   ```
   - User specifies which changes to revert
   - Keep other modifications

### Option C: Stash Work in Progress

1. **Stash All Changes**
   ```bash
   git stash push -u -m "Session cleanup - WIP from [date/description]"
   ```
   - `-u` = include untracked files
   - `-m` = add descriptive message
   - Preserves work for later retrieval

2. **Verify Stash Created**
   ```bash
   git stash list
   ```
   - Show all stashes
   - Confirm latest stash exists

3. **Inform User**
   - "Work stashed as: stash@{0}"
   - "Restore later with: git stash pop"
   - "Or discard with: git stash drop stash@{0}"

## Phase 3: Verification

After cleanup, confirm the workspace is clean:

1. **Check Git Status**
   ```bash
   git status
   ```
   - Should show "working tree clean"
   - Or only intentionally kept files

2. **List Remaining Files**
   ```bash
   git ls-files --others --exclude-standard
   ```
   - Show any remaining untracked files
   - Verify expected state

3. **Confirm to User**
   ```
   ✅ Workspace cleaned:
   - X files removed
   - Y changes reverted
   - Working tree: clean

   Ready for next session!
   ```

## Phase 4: Optional - Clean Build Artifacts

If the project has build artifacts, offer to clean those too:

1. **Check for Build Directories**
   Common patterns:
   - `dist/`, `build/`, `.next/`, `.nuxt/`
   - `node_modules/` (if re-installing)
   - `.cache/`, `.turbo/`

2. **Clean Build Artifacts**
   ```bash
   npm run clean  # if script exists
   # OR
   rm -rf dist/ build/ .next/
   ```

3. **Optionally Re-install Dependencies**
   ```bash
   npm ci  # clean install from lockfile
   ```

## User Interaction Points

This workflow requires user input at these points:

1. **After assessment**: "Found X files. Clean all, selective, stash, or cancel?"
2. **If selective**: "Which files should I remove/revert? (provide list or patterns)"
3. **After cleanup**: "Workspace cleaned. Also clean build artifacts?"
4. **If stashing**: "Add a description for this stash? (optional)"

## Safety Checks

**NEVER:**
- ❌ Clean without showing user what will be affected
- ❌ Remove tracked files (only untracked)
- ❌ Delete .git directory
- ❌ Clean if there are unpushed commits (warn user)
- ❌ Remove .env files without explicit confirmation (may contain important config)

**ALWAYS:**
- ✅ Show full list of files to be affected
- ✅ Ask for confirmation before destructive actions
- ✅ Offer stash option for work in progress
- ✅ Verify git status after cleanup
- ✅ Warn if removing large files or many files
- ✅ Respect .gitignore patterns when cleaning

## Special Cases

### Case 1: Unpushed Commits
If user has local commits not pushed to remote:
```bash
git log origin/main..HEAD --oneline
```
**Action:** Warn user and ask if they want to push first or proceed anyway

### Case 2: Untracked .env Files
If `.env`, `.env.local`, etc. are untracked:
**Action:** "Found .env files. These may contain important configuration. Keep them?"

### Case 3: Large Untracked Files
If untracked files are very large (>10MB):
**Action:** "Found large files (X MB). List them before removing?"

### Case 4: Empty Workspace
If already clean:
```
✓ Workspace is already clean
- No untracked files
- No uncommitted changes
- Ready for work!
```

## Example Session Flow

```
User: "/ta:clean-session"
Assistant: Checking workspace status...

Found:
- 3 untracked files:
  - CLAUDE.md (untracked)
  - temp-notes.txt (untracked)
  - experiments/test.html (untracked)

- 2 modified files:
  - ta/README.md (modified)
  - src/index.js (modified)

How would you like to proceed?
1. Clean all - Remove all untracked, revert all changes
2. Selective - Choose what to remove/revert
3. Stash - Save work in progress for later
4. Cancel - Keep everything

User: "Clean all"
Assistant: Cleaning workspace...

[Runs git clean -fd]
Removed: CLAUDE.md, temp-notes.txt, experiments/test.html

[Runs git restore .]
Reverted: ta/README.md, src/index.js

[Runs git restore --staged .]
Unstaged: (no files were staged)

[Runs git status]
✅ Workspace cleaned:
- 3 files removed
- 2 changes reverted
- Working tree: clean

Ready for next session!
```

## Related Commands

- `/ta:commit-and-push` - Commit work before cleaning (save progress)
- `/ta:development-analyst` - Analyze session before cleanup (preserve learnings)
- `git stash` - Built-in git command for temporary storage

## Notes for Future Development

This workflow can be enhanced with:
- Automatic backup before destructive operations
- Integration with /ta:development-analyst to auto-save session notes
- Smart detection of important untracked files (docs, configs)
- Cleanup profiles (aggressive, conservative, custom)
- Dry-run mode to preview what would be removed
