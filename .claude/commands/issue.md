# Claude Code User Command: Issue

This command helps you analyze and fix GitHub issues specified in $ARGUMENTS following GitHub flow best practices.

## Usage

To analyze and fix the GitHub issue, just type:

```
/issue <issue-number>
```

## What This Command Does

1. Analyzes the GitHub issue specified in $ARGUMENTS using GitHub CLI (`gh`).
2. Researches prior work and creates a development plan in a scratchpad.
3. Selects appropriate workflow based on issue type (standard, exploration, test-first, or rapid prototyping).
4. Creates a feature branch and implements the solution with incremental commits.
5. Tests the changes and opens a PR for review.

## Agents Used

This command leverages specialized agents based on issue type and complexity:

- **general-fullstack-developer** - For end-to-end feature implementation spanning multiple layers
- **general-backend-developer** - For API-focused issues and backend development
- **general-frontend-developer** - For UI/UX issues and frontend implementation
- **general-qa** - For comprehensive testing strategies and validation
- **general-purpose** - For complex issue analysis and multi-step research

The appropriate agent is selected based on the issue requirements and project architecture. Each agent contributes specialized expertise to ensure thorough project analysis and high-quality documentation generation.

Follow these steps:

## General

Follow these best practices and tools throughout the process:

- Follow GitHub flow in the process whenever possible - https://docs.github.com/en/get-started/using-github/github-flow
- Use the `/commit` command consistently throughout development to maintain high-quality commit messages and conventional commit standards
- Consider using context7 (https://github.com/upstash/context7) via MCP throughout the development process to capture important context, decisions, and progress. This helps with task continuity, collaboration, and knowledge preservation.
- Identify the project's browser automation tool for UI testing. Ask if you're unsure whether to use puppeteer, playwright, selenium, or another tool.
- Remember to use the GitHub CLI (`gh`) for all GitHub-related tasks.

## Workflow

While the standard workflow is: PLAN ➡️ CREATE ➡️ TEST ➡️ DEPLOY, adapt your approach based on the issue type:

- **Standard workflow** (for feature implementation): PLAN ➡️ CREATE ➡️ TEST ➡️ DEPLOY
- **Exploration workflow** (for research/investigation issues): Explore ➡️ Plan ➡️ Confirm ➡️ Code ➡️ Commit
- **Test-first workflow** (for bug fixes or TDD): Test ➡️ Commit ➡️ Code ➡️ Iterate ➡️ Commit
- **Rapid prototyping workflow** (for UI/UX issues) - Code ➡️ Screenshot ➡️ Iterate

Choose the workflow that best fits the issue requirements and adjust as needed.

## Plan

Follow these steps to understand and plan your approach:

1. Use `gh issue view` to get the issue details.
2. Understand the problem described in the issue.
3. Ask clarifying questions if necessary.
4. Understand the prior art for this issue:
    - Search the scratchpads for previous thoughts related to the issue.
    - Search PRs to see if you can find history on this issue.
    - Search the codebase for relevant files.
5. Think harder about how to break the issue down into a series of small, manageable tasks.
6. Document your plan in a new scratchpad:
    - Include the issue name in the filename.
    - Include a link to the issue in the scratchpad.

## Create

Implement the solution following these steps:

1. Create a new branch for the issue.
2. Solve the issue in small, manageable steps, according to your plan.
3. Use the /commit command to create well-formatted commits after each step.

## Commit Guidelines

When implementing changes for GitHub issues, use the `/commit` command to maintain consistency and follow conventional commit standards:

### Benefits of Using /commit
- **Automatic formatting**: Follows conventional commit format with proper issue linking
- **Consistent messages**: Ensures all commits follow the same structure and quality
- **Automatic staging**: Handles git add operations intelligently
- **Issue integration**: Automatically formats commits with issue numbers and names
- **Quality assurance**: Analyzes changes to suggest appropriate commit messages

### Integration with Issue Workflow
- Use `/commit` after each logical step in your implementation
- The command will automatically detect the GitHub issue context
- Commit messages will follow the format: `<type>: (#<issue_number>) <issue_name> - <description>.`
- For complex changes, `/commit` can suggest breaking into multiple commits

### Best Practices
- Commit frequently using `/commit` to maintain clear development history
- Each commit should represent a logical unit of work
- Let `/commit` analyze your changes and suggest appropriate commit messages
- Review the generated commit message before confirming

## Test

Verify your changes work correctly:

1. Test UI changes using available browser automation tools via MCP if you have made changes to the UX.
2. Write automated tests to describe the expected behavior of your code.
3. Run the full test suite to ensure you haven't broken anything.
4. If the tests are failing, fix them.
5. Ensure that all tests are passing before moving on to the next step.

## Best Practices for PRs

IMPORTANT: When creating pull requests, always follow these guidelines:

- **PR Title**: Use the first (most significant) commit message from the branch as the PR title.
- **PR Description**: GitHub will automatically populate the PR description using the template specified in [GitHub PR Template](#GitHub-PR-Template)
- **Format**: Follow the template structure exactly as specified in the [GitHub PR Template](#GitHub-PR-Template)
- **Requirements**: Review the requirements listed at the bottom of the [GitHub PR Template](#GitHub-PR-Template) before submitting

### GitHub PR Template
The repository includes a standardized PR template at @.github/pull_request_template.md that provides:
- Structured format for Summary, Test plan, Key Changes, and Verification sections
- Clear requirements and formatting guidelines
- Consistent format across all pull requests

When creating a PR, the template will automatically appear - simply fill in the relevant sections according to your changes.

## Deploy

Prepare your changes for review and merge:

1. Open a PR following the PR format requirements above and request a review.