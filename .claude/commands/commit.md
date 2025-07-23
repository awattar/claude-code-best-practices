# Claude Code User Command: Commit

This command helps you create well-formatted commits with conventional commit messages.

## Usage

To create a commit, just type:
```
/commit
```

## What This Command Does

1. Checks which files are staged with `git status`.
2. If 0 files are staged, automatically adds all modified and new files with `git add`.
3. Performs a `git diff` to understand what changes are being committed.
4. Analyzes the diff to determine if multiple related logical changes are present.
5. If multiple related changes are detected, breaks the commit message into multiline message.

## Best Practices for Commits

The `/commit` command follows standardized commit conventions and best practices. For detailed formatting rules and guidelines, refer to:

### Commit Format Templates
- **Format reference**: @.gitmessage - Complete commit message format specification with examples
- **Best practices**: @.github/COMMIT_CONVENTION.md - Detailed guidelines for atomic commits, splitting commits, and workflow integration

### Key Conventions
- **Conventional commit format**: Follows standardized format with issue linking
- **Atomic commits**: Each commit serves a single logical purpose
- **Format enforcement**: Automatic validation of commit message structure
- **Issue integration**: Automatic detection and formatting of GitHub issue references

### Setup Git Template (Optional)
To use the commit message template with standard git commands:
```bash
git config commit.template .gitmessage
```

This will populate the commit message editor with the template format when using `git commit` without the `-m` flag.

## Important Notes

- If specific files are already staged, the command will only commit those files.
- If no files are staged, it will automatically stage all modified and new files.
- The commit message will be constructed based on the changes detected.
- Before committing, the command will review the diff to identify if multiple commits would be more appropriate.
- If suggesting multiple commits, it will help you stage and commit the changes separately.
- Always reviews the commit diff to ensure the message matches the changes.