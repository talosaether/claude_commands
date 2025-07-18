# Claude Commands

A collection of powerful prompt templates and workflows for Claude Code to enhance productivity in software development tasks.

## Overview

This repository contains carefully crafted prompts and methodologies that help Claude Code perform complex software engineering tasks more effectively. These templates leverage Claude Code's capabilities to search codebases, analyze problems, and implement solutions systematically.

## Available Commands

### 1. Experiment-Driven Development (`01_experiment_driven_development.md`)

A structured approach for implementing code changes with a learn-from-failure methodology. This template encourages experimental development with clear tracking of attempts and learnings.

**Key Features:**
- Goal-focused planning that emphasizes impact
- Systematic learning from existing code
- Structured experiment tracking with success/failure analysis
- Iterative improvement process with balance tracking

**When to Use:**
- Complex features requiring exploration
- Bug fixes where the root cause is unclear
- Performance optimizations needing experimentation
- Refactoring with uncertain outcomes

### 2. Generate Codebase Context (`02_generate_codebase_context.md`)

A simple prompt for generating comprehensive documentation files (like `llms.txt`) that provide complete context about a codebase.

**Output Includes:**
- High-level goals for each file
- Function signatures with types and parameters
- Concise function explanations
- ASCII architecture diagrams
- Code style guide insights
- Data format documentation

**When to Use:**
- Onboarding new team members or AI assistants
- Creating codebase documentation
- Preparing context for large refactoring
- Generating reference materials

### 3. Analyze GitHub Issue (`03_analyze_github_issue.md`)

A template for analyzing GitHub issues and creating comprehensive implementation plans without actually implementing the changes.

**Process:**
1. Review GitHub issue details
2. Examine relevant codebase sections
3. Create descriptive feature branch
4. Develop comprehensive implementation plan
5. Request approval before proceeding

**Plan Considerations:**
- Required code changes and impacts
- Test strategy and documentation needs
- Performance and security implications
- Backwards compatibility
- Edge cases and best practices

**When to Use:**
- Starting work on new GitHub issues
- Planning complex implementations
- Getting stakeholder buy-in before coding
- Ensuring thorough understanding before implementation

### 4. Create GitHub Issue (`04_create_github_issue.md`)

A sophisticated template for creating well-structured GitHub issues with customizable detail levels. Emphasizes research and best practices.

**Detail Levels:**
- **MINIMAL**: Quick issues for simple bugs/features
- **MORE**: Standard issues with technical considerations
- **A LOT**: Comprehensive issues for major features

**Key Features:**
- Repository convention research
- External best practices integration
- Framework documentation lookup
- Stakeholder analysis
- Cross-referencing and formatting best practices
- AI-era development considerations

**When to Use:**
- Creating new feature requests
- Documenting bugs with reproduction steps
- Planning architectural changes
- Proposing improvements or refactors

### 5. Resolve PR Comments (`05_resolve_pr_comments.md`)

An advanced workflow for systematically resolving all comments, to-dos, and issues in pull requests. Includes parallel processing capabilities for faster resolution.

**Workflow Phases:**
1. **Research & Analysis**: Comprehensive comment discovery
2. **Planning**: Prioritized action items with TodoWrite tracking
3. **Implementation**: Systematic resolution of all items
4. **Verification**: Quality assurance and testing

**Advanced Features:**
- Parallel sub-agent coordination for independent changes
- Intelligent comment classification by priority
- Comprehensive GitHub API usage examples
- Resolution tracking and verification

**When to Use:**
- Addressing code review feedback
- Resolving multiple PR comments efficiently
- Cleaning up to-dos before merging
- Responding to review requests systematically

## Usage

Each command is designed to be used with Claude Code's slash command feature or copied directly into conversations. The templates use placeholder syntax like `#$ARGUMENTS` for dynamic content insertion.

### Example Usage:

```bash
# Using as a slash command
/research Create a feature for user authentication with OAuth

# Or copy the template content directly and replace placeholders
```

## Best Practices

1. **Choose the Right Template**: Select templates based on task complexity and requirements
2. **Provide Clear Context**: Include relevant details when using templates
3. **Follow the Phases**: Templates often have multiple phases - complete each thoroughly
4. **Use TodoWrite**: Leverage Claude Code's task tracking for complex workflows
5. **Verify Results**: Always run tests and linting after making changes

## Benefits

- **Consistency**: Standardized approaches to common tasks
- **Efficiency**: Reduced time spent on planning and research
- **Quality**: Built-in best practices and comprehensive considerations
- **Learning**: Structured experimentation with documented outcomes
- **Collaboration**: Clear communication through well-structured issues and PRs

## Contributing

Feel free to add new command templates or improve existing ones. Follow these guidelines:
- Keep templates focused on specific use cases
- Include clear documentation and examples
- Consider both simple and complex scenarios
- Add helpful thinking prompts and checklists
- Test templates thoroughly before committing

## Tips for Effective Use

1. **Customize for Your Project**: Adapt templates to match your team's conventions
2. **Combine Templates**: Use multiple templates together for complex workflows
3. **Store Custom Versions**: Save project-specific variations in `.claude/commands/`
4. **Share with Team**: Ensure consistent approaches across your development team
5. **Iterate and Improve**: Refine templates based on real-world usage

## Future Enhancements

Potential areas for new command templates:
- Database migration planning
- API design and documentation
- Security audit workflows
- Performance optimization strategies
- Deployment and rollback procedures
- Code review templates
- Technical debt tracking

---

These Claude Commands help transform Claude Code from a coding assistant into a comprehensive software engineering partner, capable of handling complex workflows with consistency and intelligence.