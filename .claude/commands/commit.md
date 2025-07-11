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

- **Atomic commits**: Each commit should contain related changes that serve a single purpose (feature subtask, issue fix, documentation or configuration changes, etc.).
- **Split large changes**: If changes touch multiple concerns, split them into separate description lines.
- **Conventional commit format** (MUST FOLLOW EXACTLY): Use the format `<type>: (#<issue_number>) <issue_name> - <description>.` or `<type>: <description>.` when GitHub issue cannot be identified:
  - Where `<type>` is one of:
    - `New feature`: A new feature.
    - `Fix issue`: A bug fix.
    - `Other`: Other changes (documentation, configuration, etc.).
  - Where `<issue_number>` is the GitHub issue number.
  - Where `<issue_name>` is GitHub issue name.
  - Where `<description>` is generated commit message.
  - Line MUST end with a `.` (dot).
- **Multiline commit format** (MUST FOLLOW EXACTLY): Use the format  

  ```
  <type>: (#<issue_number>) <issue_name>:
  - <description_line_1>.
  - <description_line_2>.
  - ...
  ```

  or use format when current issue is sub-issue of another issue:

  ```
  <type>: (#<parent_issue_number>) <parent_issue_name>:
  - (#<issue_number>) <issue_name>.
  - <description_line_1>.
  - <description_line_2>.
  - ...
  ```

  - Where `<parent_issue_number>` is the parent GitHub issue number.
  - Where `<parent_issue_name>` is the parent GitHub issue name.
  - Where `<issue_number>` is the GitHub issue number.
  - Where `<issue_name>` is GitHub issue name.
  - Where `<description_line_X>` represents a message for a different concern.
  - The first line MUST end with a `:` (colon).
  - Each bullet point MUST end with a `.` (period).
  - Each bullet point MUST start with `- ` (dash and space).
- **Present tense, imperative mood**: Write commit messages as commands (e.g., "add feature" not "added feature").
- **No additional content**: NEVER add any extra content to commit messages such as "Generated with Claude Code", author information, or any other additions beyond the specified format.

## Guidelines for Splitting Commits

When analyzing the diff, suggest splitting commits based on these criteria:

1. **Unrelated concerns**: Changes to unrelated parts of the codebase.
2. **Different types of changes**: Mixing features, fixes, major refactoring, etc.
3. **File patterns**: Changes to different types of files (e.g., source code vs documentation).
4. **Logical grouping**: Changes that would be easier to understand or review separately.
5. **Size**: Very large changes that would be clearer if broken down.

## Important Notes

- If specific files are already staged, the command will only commit those files.
- If no files are staged, it will automatically stage all modified and new files.
- The commit message will be constructed based on the changes detected.
- Before committing, the command will review the diff to identify if multiple commits would be more appropriate.
- If suggesting multiple commits, it will help you stage and commit the changes separately.
- Always reviews the commit diff to ensure the message matches the changes.