---
name: conventional-commits
description: Use when writing git commit messages in this repository. Enforces the project's conventional commit format — type prefix, GitHub issue reference, and atomic commits — as defined in .gitmessage and .github/COMMIT_CONVENTION.md.
---

# Conventional Commits

When creating any git commit in this repository, follow the project's commit convention.
Unlike the `/commit` command (which the user invokes explicitly), this skill applies
automatically whenever a commit message is being authored.

## Format

Single-line, when a GitHub issue applies:

    <type>: (#<issue_number>) <issue_name> - <description>.

Single-line, when no GitHub issue applies:

    <type>: <description>.

Multiline, when the change spans multiple concerns:

    <type>: (#<issue_number>) <issue_name>:
    - <description_line_1>.
    - <description_line_2>.

## Rules

- `<type>` is exactly one of: `New feature`, `Fix issue`, `Other`.
- Single-line messages end with `.`; the first line of a multiline message ends with `:`.
- Every bullet starts with `- ` and ends with `.`.
- Use present tense, imperative mood ("add feature", not "added feature").
- Keep commits atomic — one logical concern per commit. Split unrelated changes into
  separate commits.
- NEVER add trailers such as "Generated with Claude Code", author info, or co-author lines.

## References

- Full template with examples: `.gitmessage`
- Commit-splitting guidance and workflow integration: `.github/COMMIT_CONVENTION.md`
- For an interactive, guided commit flow, use the `/commit` command.
