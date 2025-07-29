# Claude Code User Command: Reviewpr

This command helps you thoroughly review GitHub pull requests specified in $ARGUMENTS.

## Usage

To review a pull request, just type:

```
/reviewpr <pr-number>
```

## What This Command Does

1. Fetches PR details and diff for $ARGUMENTS using GitHub CLI (`gh`).
2. Checks CI/CD status and checks out the PR locally.
3. Reviews code quality, observability, and tests the changes.
4. Documents findings in a scratchpad and submits review via GitHub CLI (`gh`).
5. Monitors for author responses and re-reviews as needed.

## Agents Used

This command leverages specialized agents for comprehensive pull request review:

- **general-code-quality-debugger** - Essential for systematic code review and quality assessment
- **general-technical-project-lead** - For security assessments and architectural review
- **general-qa** - For testing validation and edge case identification
- **general-solution-architect** - For reviewing architectural decisions and patterns

Each agent contributes specialized expertise to ensure thorough project analysis and high-quality documentation generation.

Follow these steps:

## General

Follow GitHub flow and code review best practices - https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests

Before starting:

- Identify the project's test framework and browser automation tools (e.g., puppeteer, playwright, selenium) for testing UI change via MCP. Check project documentation or ask if unclear.
- Remember to use the GitHub CLI (`gh`) for all PR-related tasks.

## Analyze

Gather context and understand the PR:

1. Use `gh pr view` to get the PR details and description.
2. Use `gh pr diff` to review the changes in detail.
3. Check the PR against the original issue requirements:
    - Use `gh pr view --json body,title,number` to get linked issues.
    - Verify all acceptance criteria are met.
4. Search scratchpads for any design decisions or context related to this PR.
5. Use `gh pr checks` to verify CI/CD status.

## Review

Examine the code quality and functionality:

1. Check out the PR locally using `gh pr checkout`.
2. Review code quality:
    - Look for potential bugs or edge cases.
    - Verify naming conventions and code style.
    - Check for proper error handling.
    - Assess performance implications.
3. Review observability aspects:
    - Verify appropriate logging is added for debugging and monitoring.
    - Check error handling includes meaningful log messages.
    - Ensure new features have metrics/instrumentation where needed.
    - Confirm sensitive data is not exposed in logs.
    - Review if critical paths have proper monitoring hooks.
4. Test the changes:
    - Run the test suite with focus on affected areas.
    - Use browser automation tools via MCP for UI changes.
    - Manually test critical paths.
5. Review documentation:
    - Ensure code comments are clear and helpful.
    - Check if README or other docs need updates.
    - Verify any new logging/monitoring is documented.

## Provide Feedback

Document and communicate your findings:

1. Document findings in a scratchpad:
    - Include PR number and title in filename.
    - List issues found with severity (blocking/suggestion).
    - Provide specific code suggestions where applicable.
2. If fixes are needed:
    - Create commits with suggested changes.
    - Push to a separate branch if significant changes.
3. Use `gh pr review` to submit your review:
    - Approve if all checks pass.
    - Request changes with specific feedback.
    - Comment for clarifications or discussions.

## Iterate

Follow up on the review process:

1. Monitor PR for author responses using `gh pr view --comments`.
2. Re-review after changes are made.
3. Approve once all concerns are addressed.

Remember to be constructive and specific in feedback, focusing on the code not the person.