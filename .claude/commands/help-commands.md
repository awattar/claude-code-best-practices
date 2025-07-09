# Claude Code User Command: Help Commands

This command provides comprehensive help for all available custom commands in this Claude Code Best Practices repository.

## Usage

To get help with available commands, just type:

```
/help-commands
```

## Available Commands

- `/custom-init` - CLAUDE.md Generator.
- `/commit` - Conventional Commits.
- `/issue` - GitHub Issue Workflow.
- `/reviewpr` - Pull Request Review.
- `/test` - Test Suite Management.

## How It Works

### `/custom-init` - CLAUDE.md Generator

- **Purpose**: Automatically generates comprehensive CLAUDE.md files for any project.
- **Usage**: `/custom-init`
- **What it does**: 
  - Analyzes project structure and detects technology stack.
  - Generates documentation sections (Overview, Architecture, Features).
  - Creates development workflow guides.
  - Produces comprehensive project context for AI assistants.
- **Best for**: New projects, onboarding, or updating existing documentation.

### `/commit` - Conventional Commits

- **Purpose**: Creates well-formatted conventional commits following best practices.
- **Usage**: `/commit`
- **What it does**:
  - Analyzes staged changes (or stages all changes if none staged).
  - Generates conventional commit messages.
  - Suggests splitting large commits into smaller, atomic ones.
  - Follows format: `<type>: <github_issue> - <description>`.
- **Best for**: Maintaining clean git history and following team conventions.

### `/issue` - GitHub Issue Workflow

- **Purpose**: End-to-end GitHub issue resolution following GitHub Flow.
- **Usage**: `/issue <issue-number>`
- **What it does**:
  - Analyzes GitHub issues using `gh` CLI.
  - Creates development plans and feature branches.
  - Implements solutions with incremental commits.
  - Handles testing and PR creation.
- **Best for**: Structured issue resolution and feature development.

### `/reviewpr` - Pull Request Review

- **Purpose**: Comprehensive PR review process with quality checks.
- **Usage**: `/reviewpr <pr-number>`
- **What it does**:
  - Fetches PR details and analyzes changes.
  - Checks CI/CD status and code quality.
  - Reviews observability, testing, and documentation.
  - Provides structured feedback via GitHub CLI.
- **Best for**: Code reviews, quality assurance, and team collaboration.

### `/test` - Test Suite Management

- **Purpose**: Comprehensive test execution and improvement.
- **Usage**: `/test <scope>` or `/test all`
- **What it does**:
  - Identifies test framework and browser automation tools.
  - Runs targeted or full test suites.
  - Fixes failing tests and adds missing coverage.
  - Provides detailed reporting and improvement suggestions.
- **Best for**: TDD workflows, CI/CD validation, and test maintenance.

## Usage Examples

### Using Custom Commands

```bash
# Create a conventional commit
/commit

# Generate CLAUDE.md for any project
/custom-init

# Work on a GitHub issue
/issue 123

# Review a pull request
/reviewpr 456

# Run tests for specific scope
/test src/components/
```

## Best Practices

### Command Usage

- **Start with `/custom-init`** for new projects to establish proper documentation.
- **Use `/issue`** for structured feature development and bug fixes.
- **Run `/test`** before commits to ensure code quality.
- **Always use `/commit`** for consistent commit messages.
- **Use `/reviewpr`** for thorough code reviews.

### Workflow Integration

- Follow GitHub Flow: issue ➡️branch ➡️ develop ➡️ test ➡️ PR ➡️ review ➡️ merge.
- Use commands in sequence for complex tasks.
- Document decisions in scratchpads created by commands.
- Maintain atomic commits for better history and easier rollbacks.

### Project Setup

- Ensure GitHub CLI is authenticated and configured.
- Identify and document project-specific testing tools.
- Set up browser automation for UI testing.
- Configure project-specific conventions in documentation.