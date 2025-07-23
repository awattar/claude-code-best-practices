# Commit Convention and Best Practices

## Best Practices for Commits

### Atomic Commits
- **Atomic commits**: Each commit should contain related changes that serve a single purpose (feature subtask, issue fix, documentation or configuration changes, etc.).
- **Split large changes**: If changes touch multiple concerns, split them into separate description lines.

### Commit Message Style
- **Present tense, imperative mood**: Write commit messages as commands (e.g., "add feature" not "added feature").
- **No additional content**: NEVER add any extra content to commit messages such as "Generated with Claude Code", author information, or any other additions beyond the specified format.

## Guidelines for Splitting Commits

When analyzing the diff, suggest splitting commits based on these criteria:

1. **Unrelated concerns**: Changes to unrelated parts of the codebase.
2. **Different types of changes**: Mixing features, fixes, major refactoring, etc.
3. **File patterns**: Changes to different types of files (e.g., source code vs documentation).
4. **Logical grouping**: Changes that would be easier to understand or review separately.
5. **Size**: Very large changes that would be clearer if broken down.

## Commit Format Reference

For detailed commit message formatting rules and examples, see the commit message template:
- **Template file**: @.gitmessage in the project root
- **Usage with git**: `git config commit.template .gitmessage`

## Integration with Development Workflow

### With Claude Code Commands
- Use `/commit` command for automated commit message generation following these conventions
- The `/commit` command automatically applies the format rules and best practices
- Review generated commit messages to ensure they follow the atomic commit principle

### Manual Commits
When creating commits manually, always:
1. Review the staged changes to ensure they form a logical unit
2. Follow the conventional commit format from [Commit Format Reference](#commit-format-reference)
3. Consider splitting large changesets into multiple atomic commits
4. Use descriptive, imperative mood commit messages