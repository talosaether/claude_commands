# Task Automation (TA) Commands

> Custom slash commands for automating common development workflows

**Location:** `~/.claude/commands/ta/`
**Prefix:** `/ta:` - All commands in this directory use the `/ta:` prefix

---

## Important Note for Future Claude Sessions

**When working with slash commands in this repository:**

1. **All custom commands use the `/ta:` prefix**
   - Example: `/ta:commit-and-push`, `/ta:development-analyst`
   - This distinguishes them from built-in commands

2. **Command file naming convention**
   - Filename: `command-name.md` (kebab-case)
   - Command: `/ta:command-name`
   - Example: `commit-and-push.md` → `/ta:commit-and-push`

3. **Creating new commands**
   - Place `.md` files in `~/.claude/commands/ta/`
   - Follow existing command structure (see templates below)
   - Document in this README
   - Test thoroughly before committing

4. **YAML files vs MD files**
   - `.md` files: Full prompt/workflow templates
   - `.yaml`/`.yml` files: Simplified command definitions (less common)
   - Prefer `.md` for complex workflows with examples

---

## Available Commands

### `/ta:onboard`
**File:** `onboard.md`
**Purpose:** Quick project onboarding for new Claude sessions - reads all documentation, understands context, and presents comprehensive project summary

**Philosophy:** Embodies **Compound Engineering** (Kieran Klaassen, Every) - building systems that compound in value over time through iterative improvement.

**Use when:**
- Starting a new Claude Code session
- Switching to a different project
- Need to refresh project context
- Want to understand available workflows

**What it does:**
1. Reads CLAUDE.md (project memory)
2. Reads README.md, prd.md, TODO.md
3. Analyzes git history and current state
4. Explores `~/.claude/commands/` repository
5. Checks project dependencies and structure
6. Presents comprehensive onboarding summary

**Key feature:** Encourages proactive contribution to `/ta:` workflows. When you discover useful patterns, the command prompts you to standardize them.

**Example:**
```
/ta:onboard
```

**Output:** Concise summary with:
- Project type and status
- Critical knowledge and gotchas
- Current priorities
- Available commands
- Quick start commands

---

### `/ta:commit-and-push`
**File:** `commit-and-push.md`
**Purpose:** Comprehensive git commit and push workflow with testing, detailed commit messages, and optional PR creation

**Use when:**
- Ready to commit changes with full context
- Want standardized commit message format
- Need to push and/or create PR
- Want automated testing before commit

**Workflow:**
1. Run tests and build
2. Review changes (git status, diff, log)
3. Generate detailed commit message
4. Stage and commit with HEREDOC formatting
5. Optional push to remote
6. Optional PR creation

**Example:**
```
/ta:commit-and-push
```

---

### `/ta:development-analyst`
**File:** `development-analyst.md`
**Purpose:** Analyzes development session and extracts learnings for future Claude sessions

**Use when:**
- Completing a significant work session
- Before committing major changes
- After solving complex problems
- To update project memory (CLAUDE.md)

**Outputs:**
- Session overview with outcomes
- Problems solved and solutions
- Patterns established
- User preferences discovered
- System relationships mapped
- Knowledge updates for CLAUDE.md

**Example:**
```
/ta:development-analyst
```

---

### `/ta:test-driven-debug`
**File:** `test-driven-debug.md`
**Purpose:** Systematic test-driven debugging workflow for fixing broken features

**Use when:**
- Feature is broken and needs fixing
- Implementing new functionality with reliability requirements
- Debugging complex integration issues
- Need comprehensive solution documentation

**Workflow:**
1. Set up test infrastructure
2. Write comprehensive tests BEFORE fixing
3. Debug iteratively using test failures
4. Validate solution with all tests passing
5. Document comprehensively
6. Commit with full context

**Example:**
```
/ta:test-driven-debug
```

---

### `/ta:deployment-agent`
**File:** `deployment-agent.md`
**Purpose:** Handles deployment workflows and processes

**Use when:**
- Deploying to production/staging
- Managing deployment pipelines
- Coordinating releases

**Example:**
```
/ta:deployment-agent
```

---

## Command Template Structure

When creating new `/ta:` commands, follow this structure:

```markdown
You are implementing a [NAME OF WORKFLOW]. This command guides you through [BRIEF DESCRIPTION].

## Workflow Overview

This workflow [PURPOSE AND GOALS]:
- Key benefit 1
- Key benefit 2
- Key benefit 3

## Phase 1: [FIRST PHASE NAME]

[Description of what happens in this phase]

1. **Step 1 Name**
   ```bash
   command example
   ```
   - Detail 1
   - Detail 2
   - Detail 3

2. **Step 2 Name**
   [Instructions...]

## Phase 2: [SECOND PHASE NAME]

[Continue with clear phases...]

## User Interaction Points

This workflow requires user input at these points:
1. [When and what to ask]
2. [When and what to ask]

## Safety Checks

**NEVER:**
- ❌ Thing to avoid 1
- ❌ Thing to avoid 2

**ALWAYS:**
- ✅ Thing to always do 1
- ✅ Thing to always do 2

## Example Session Flow

\`\`\`
User: "Request example"
Assistant: [Full example of command execution]
\`\`\`

## Related Commands

- `/ta:other-command` - When to use instead
- Built-in command - How it relates

## Notes for Future Development

[Ideas for enhancing this command]
```

---

## Best Practices for TA Commands

### 1. Clear Phase Structure
- Break workflow into distinct phases
- Number steps within each phase
- Show progression clearly

### 2. Code Examples
- Provide actual command examples
- Show expected output
- Include error handling

### 3. Safety Checks
- List what to NEVER do
- List what to ALWAYS do
- Explain why for critical items

### 4. User Interaction
- Clarify when user input needed
- Provide example questions to ask
- Show decision points

### 5. Context Preservation
- Document decisions made
- Explain trade-offs chosen
- Reference related patterns

---

## Naming Conventions

### Command Names (kebab-case)
- `commit-and-push` ✅
- `development-analyst` ✅
- `test-driven-debug` ✅
- `commitAndPush` ❌ (wrong case)
- `commit_and_push` ❌ (wrong separator)

### File Names
- Match command name exactly
- Use `.md` extension for full templates
- Use `.yaml`/`.yml` for simple definitions

### Slash Command Usage
- Always use `/ta:` prefix
- Lowercase command name
- Hyphens for multi-word commands

---

## Testing New Commands

Before committing a new `/ta:` command:

1. **Test the workflow**
   - Run through entire command manually
   - Verify all steps work as documented
   - Check error handling

2. **Validate examples**
   - Ensure code examples are correct
   - Test commands actually run
   - Verify output matches documentation

3. **Check formatting**
   - Markdown renders correctly
   - Code blocks use proper syntax highlighting
   - Lists and bullets display properly

4. **Review safety**
   - No destructive commands without warnings
   - User confirmation for risky operations
   - Clear rollback procedures

---

## Integration with Other Systems

### CLAUDE.md
- `/ta:development-analyst` outputs → Update CLAUDE.md
- Document new patterns established
- Reference command decisions

### Git Workflow
- `/ta:commit-and-push` → Standardized commits
- Detailed context preserved
- Co-authorship tracked

### Project Documentation
- Commands reference project docs
- Update docs when commands evolve
- Keep examples synchronized

---

## Future Command Ideas

Potential new `/ta:` commands to develop:

- `/ta:refactor-plan` - Plan and execute safe refactoring
- `/ta:performance-audit` - Analyze and optimize performance
- `/ta:security-scan` - Check for security vulnerabilities
- `/ta:dependency-update` - Update and test dependencies
- `/ta:api-design` - Design API endpoints systematically
- `/ta:database-migration` - Create and test DB migrations

---

## Troubleshooting

### Command not found
**Problem:** `/ta:command-name` not recognized
**Solution:**
1. Check file exists in `~/.claude/commands/ta/`
2. Verify filename matches command (kebab-case)
3. Ensure `.md` extension
4. Restart Claude Code if needed

### Command runs but workflow unclear
**Problem:** Not sure what to do next
**Solution:**
1. Read the "Workflow Overview" section
2. Check "Example Session Flow"
3. Follow phases sequentially
4. Ask user for clarification when needed

### Want to modify a command
**Process:**
1. Edit the `.md` file in `~/.claude/commands/ta/`
2. Test the modified workflow
3. Update this README if adding new features
4. Commit changes with clear message

---

## Contributing

When adding new `/ta:` commands:

1. **Research existing commands** - Avoid duplication
2. **Follow template structure** - Maintain consistency
3. **Write comprehensive examples** - Show full workflow
4. **Test thoroughly** - Verify all steps work
5. **Document in README** - Add to this file
6. **Commit with context** - Explain why command was added

---

**Repository:** `~/.claude/commands/` (git-tracked)
**Last Updated:** 2025-10-03
**Maintained By:** User + Claude Code collaboration
