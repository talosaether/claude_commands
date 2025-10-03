You are onboarding to a new project session. This command helps you quickly understand the project context, patterns, and workflows established in previous sessions.

## Philosophy: Compound Engineering

This workflow embodies **Compound Engineering** - a concept from Kieran Klaassen at Every. The core idea: engineering work should compound in value over time through iterative improvement of shared systems, patterns, and documentation.

**Key Principles:**
1. **Build reusable systems** - Not just one-off solutions
2. **Document patterns** - Make knowledge transferable
3. **Iterate and refine** - Test-driven refactoring of workflows
4. **Create contracts** - Establish agreements on how we work
5. **Compound value** - Each session builds on the last

The `claude_commands` repository (`~/.claude/commands/`) is our **interface for developing contracts** - loose agreements and suggestions on software development lifecycle. It's an **iterable body of work**, ripe for consistent improvement.

**Your role:** Be proactive about:
- Contributing new `/ta:*` commands when you discover useful patterns
- Refining existing workflows based on session learnings
- Standardizing approaches that work well
- Documenting decisions for future sessions

## Onboarding Workflow

### Phase 1: Read Core Project Documentation

Read these files in order to understand the project:

1. **CLAUDE.md** (if exists)
   - This is the **primary source of truth** for project context
   - Contains critical knowledge, patterns, decisions
   - Session history and lessons learned
   - Read this FIRST and COMPLETELY

2. **README.md** (project root)
   - Project overview and setup instructions
   - Key features and architecture
   - Development workflow

3. **prd.md** or **PRD.md** (if exists)
   - Product requirements and goals
   - Feature specifications
   - Success metrics

4. **TODO.md** (if exists)
   - Current priorities and tasks
   - Known issues
   - Future improvements planned

5. **docs/** directory
   - Scan for implementation guides
   - Look for pattern libraries
   - Check for troubleshooting docs

### Phase 2: Understand Git History

Run these commands to understand recent work:

```bash
git log --oneline -20
git status
git branch -a
```

**What to look for:**
- Recent commit patterns (what's been worked on)
- Commit message style (how to format your commits)
- Active branches (ongoing work)
- Current state (clean or in-progress)

### Phase 3: Explore the Claude Commands Repository

The commands repository is at `~/.claude/commands/` - this is crucial!

1. **Read the main README**
   ```bash
   cat ~/.claude/commands/README.md
   ```

2. **Read the `/ta:` directory README**
   ```bash
   cat ~/.claude/commands/ta/README.md
   ```

3. **List available `/ta:` commands**
   ```bash
   ls -la ~/.claude/commands/ta/
   ```

4. **Understand available workflows**
   - `/ta:commit-and-push` - Standardized git workflow
   - `/ta:development-analyst` - Session analysis and learning extraction
   - `/ta:test-driven-debug` - Systematic debugging workflow
   - `/ta:deployment-agent` - Deployment processes
   - Others as they're added

**Key insight:** These commands are **living documentation** of how we work together. When you discover a useful pattern during a session, you should proactively suggest creating a new `/ta:` command or improving an existing one.

### Phase 4: Check Project Dependencies & Setup

Run these to verify environment:

```bash
# Check package.json for project type and scripts
cat package.json | grep -A 10 "scripts"

# Check for test framework
npm test -- --help 2>/dev/null || echo "No test command"

# Check for build process
npm run build --help 2>/dev/null || echo "No build command"

# List available npm scripts
npm run
```

### Phase 5: Understand Project Structure

Use Glob to map the codebase:

```bash
# List key directories
ls -la

# Find main source files
find src -type f -name "*.js" -o -name "*.vue" -o -name "*.ts" | head -20

# Check for tests
find . -type f -name "*.test.*" -o -name "*.spec.*" | head -10
```

### Phase 6: Synthesize and Present

After reading all context, present a **concise onboarding summary**:

```
## Project: [Name]

**Type:** [Framework/Language]
**Status:** [Current milestone/state]
**Last session:** [What was worked on]

### Critical Knowledge
- [Key architectural decision 1]
- [Key pattern 1]
- [Important gotcha 1]

### Current Priorities
- [Priority 1 from TODO.md]
- [Priority 2 from TODO.md]

### Available Commands
- `/ta:command-name` - Purpose
- `/ta:another-command` - Purpose

### Quick Start
- Dev server: `npm run dev`
- Tests: `npm test`
- Build: `npm run build`

**Ready to work!** What would you like to tackle?
```

## Proactive Contribution to `/ta:` Commands

As you work through sessions, watch for these opportunities:

### When to Create a New `/ta:` Command

1. **You repeat a multi-step process** more than once
   - Example: "Deploy to staging" involves 5+ steps
   - Solution: Create `/ta:deploy-staging`

2. **You discover a useful debugging pattern**
   - Example: Systematic approach to fixing CSS issues
   - Solution: Create `/ta:debug-css`

3. **User requests a specific workflow repeatedly**
   - Example: "Update dependencies and test"
   - Solution: Create `/ta:update-deps`

4. **You solve a complex problem with a clear process**
   - Example: Database migration workflow
   - Solution: Create `/ta:db-migrate`

### When to Refine Existing `/ta:` Commands

1. **A command is missing a step** you had to add manually
   - Suggest: "I noticed `/ta:commit-and-push` doesn't check for secrets. Should we add that?"

2. **You find a better way to do something**
   - Suggest: "We could parallelize these git commands in `/ta:commit-and-push`"

3. **A command produces unclear output**
   - Suggest: "Let's add more detailed status messages to `/ta:test-driven-debug`"

4. **Safety checks are needed**
   - Suggest: "Should `/ta:deployment-agent` verify branch name before deploying?"

### Template for Suggesting Improvements

When you identify an improvement opportunity:

```
I noticed [pattern/issue] while working on [task].

This could be a good addition to our `/ta:` workflows:

**Option A:** Create new command `/ta:proposed-name`
- Purpose: [What it does]
- When to use: [Scenarios]
- Workflow: [High-level steps]

**Option B:** Enhance existing `/ta:existing-command`
- Current gap: [What's missing]
- Proposed addition: [What to add]
- Benefit: [Why it helps]

Would you like me to draft this?
```

## Compound Engineering in Action

Each session should leave the codebase AND the workflows better:

### Codebase Compounding
- ✅ Write reusable code (not one-off hacks)
- ✅ Document patterns (CLAUDE.md, README updates)
- ✅ Create examples (experiments/ directory)
- ✅ Add tests (validate future changes)

### Workflow Compounding
- ✅ Capture useful processes as `/ta:` commands
- ✅ Refine commands based on real usage
- ✅ Document decisions in command files
- ✅ Create templates for common tasks

### Knowledge Compounding
- ✅ Update CLAUDE.md with lessons learned
- ✅ Run `/ta:development-analyst` after significant work
- ✅ Document gotchas and solutions
- ✅ Reference decisions in commits

## Example Onboarding Session

```
User: "Get up to speed on the project"
Assistant: Running /ta:onboard...

**Phase 1: Reading Core Documentation**
[Reads CLAUDE.md]
✓ Project: Yoke - Emby Media Client
✓ Architecture: Hybrid vanilla JS + Vue 3
✓ Current status: Milestone 2 complete

[Reads README.md, prd.md, TODO.md]
✓ Understanding project goals and priorities

**Phase 2: Git History**
[Runs git log, status, branch]
✓ Last commit: Text overflow handling
✓ Working tree: Clean
✓ Branch: main

**Phase 3: Claude Commands Repository**
[Reads ~/.claude/commands/README.md and ta/README.md]
✓ Found 4 /ta: commands available
✓ Understanding workflow contracts

**Phase 4: Project Setup**
[Checks package.json]
✓ Vite + Vue 3 + Vitest
✓ Dev: npm run dev (port 3001)
✓ Tests: npm test
✓ Build: npm run build

**Phase 5: Structure**
[Maps codebase]
✓ Services: Vanilla JS business logic
✓ Components: Vue 3 presentation
✓ Tests: Vitest with happy-dom

---

## Yoke - Emby Media Client

**Type:** Hybrid vanilla JS + Vue 3
**Status:** Milestone 2 complete - Dynamic filtering + Video playback
**Last session:** Added comprehensive text overflow handling

### Critical Knowledge
- Services are vanilla JS, never import Vue into them
- Video streaming uses /Items/{id}/Download endpoint (NOT /emby/Videos)
- Auth token is authData.token (NOT authData.accessToken)
- Text overflow handled with multi-layered CSS approach

### Current Priorities
- Four-tier SQLite caching system (planned)
- Web Worker prefetching (planned)
- Virtual scrolling for huge libraries (planned)

### Available Commands
- /ta:onboard - This command (project onboarding)
- /ta:commit-and-push - Standardized git workflow
- /ta:development-analyst - Session analysis
- /ta:test-driven-debug - Systematic debugging

### Quick Start
- Dev server: npm run dev (http://localhost:3001)
- Tests: npm test -- --run
- Build: npm run build
- Diagnostic tools: experiments/ directory

**Ready to work!** What would you like to tackle?
```

## Success Criteria

Onboarding is complete when you can answer:

- ✅ What is this project and what does it do?
- ✅ What architecture/patterns are used?
- ✅ What was worked on recently?
- ✅ What are current priorities?
- ✅ What commands/workflows are available?
- ✅ How do I run dev/test/build?
- ✅ Where do I find documentation?
- ✅ What are the known gotchas?

## Integration with Compound Engineering

Remember: This `/ta:onboard` command itself is part of the compounding system!

**After running onboarding:**
1. If you notice missing information → Suggest adding to CLAUDE.md
2. If workflow is unclear → Suggest refining this command
3. If you learn new patterns → Update documentation
4. If you find better approaches → Contribute back to `/ta:` commands

**The goal:** Each time a new Claude session runs `/ta:onboard`, it should be faster, clearer, and more valuable than the last time.

## Related Commands

- `/ta:development-analyst` - Run at end of session to capture learnings
- `/ta:commit-and-push` - Use when ready to commit work
- `/ta:test-driven-debug` - Use when fixing bugs systematically

## Notes for Future Enhancement

This command could be enhanced with:
- Automatic detection of project type (React vs Vue vs vanilla)
- Smart prioritization of docs (read most important first)
- Integration with GitHub issues for current work context
- Automatic dependency vulnerability check
- Project health metrics (test coverage, build time, etc.)
- Comparison with previous sessions (what changed since last time)

---

**Credits:** Compound Engineering concept by Kieran Klaassen (Every)
**Philosophy:** Build systems that compound in value over time
**Repository:** ~/.claude/commands/ (git-tracked, iterable, test-driven)

