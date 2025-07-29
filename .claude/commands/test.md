# Claude Code User Command: Test

This command helps you run and improve the test suite for the scope specified in $ARGUMENTS.

## Usage

To test specific files or features, just type:

```
/test <file-or-directory>
/test <feature>
```

To test everything, just type:

```
/test all
```

## What This Command Does

1. Identifies test scope based on $ARGUMENTS (file, directory, feature or all).
2. Checks current test coverage and runs targeted tests first.
3. Executes integration and full test suite as needed.
4. Fixes failing tests and adds missing test coverage.
5. Documents results and commits improvements.

## Agents Used

This command leverages specialized agents for comprehensive test suite management:

- **general-qa** - Primary agent for comprehensive testing strategies and automation
- **general-code-quality-debugger** - For debugging failing tests and improving test quality
- **general-backend-developer** - For API testing and integration test implementation
- **general-frontend-developer** - For UI testing with browser automation tools

Each agent contributes specialized expertise to ensure thorough project analysis and high-quality documentation generation.

Follow these steps:

## General

Follow testing best practices and TDD principles. See GitHub's language-specific testing guides at https://docs.github.com/en/actions/how-tos/use-cases-and-examples/building-and-testing

Before starting:

- Identify the project's test framework (e.g., RSpec, Jest, pytest, xUnit). Check package.json, Gemfile, requirements.txt, or project documentation.
- Determine the browser automation tool for UI tests (e.g., puppeteer, playwright, selenium, cypress). Ask if unclear.
- Identify E2E testing approach based on the application type (browser-based, API, CLI, or mixed).
- Locate test configuration files and understand the test structure.
- Check for any project-specific testing guidelines in documentation or README.

## Assess

Understand the current testing landscape:

1. Identify the scope:
    - If $ARGUMENTS is a file/directory, focus tests there.
    - If $ARGUMENTS is a feature, find all related specs.
    - If $ARGUMENTS is "all", prepare for full suite run.
2. Check current test coverage:
    - Run coverage reports if available.
    - Identify untested or poorly tested areas.
3. Review existing test patterns:
    - Search for similar test files as examples.
    - Check scratchpads for testing guidelines.

## Run Test

Execute tests to verify current state:

1. Execute targeted tests first:
    - Run specific test files/suites for the affected code.
    - Use verbose/detailed output mode for better debugging.
    - Enable fail-fast mode to stop on first failure during debugging.
2. Run related integration tests:
    - Identify integration/feature tests that touch the code.
    - Run system/e2e tests if UI or API contracts are affected.
3. Execute full test suite:
    - Run the complete test suite using the project's test command.
    - Monitor for flaky tests, timeouts, or unexpected failures.
    - Check test execution time for performance regressions.

## Improve

Enhance test coverage and quality:

1. Fix failing tests:
    - Analyze failure messages carefully.
    - Check if tests or implementation need fixing.
    - Commit fixes with clear messages.
2. Add missing tests:
    - Write tests for uncovered edge cases.
    - Add integration tests for critical paths.
    - Ensure both happy and error paths are tested.
3. Refactor existing tests:
    - Remove duplication using shared examples.
    - Improve test descriptions for clarity.
    - Speed up slow tests where possible.

## Validate

Ensure all improvements are working correctly:

1. Verify improvements:
    - Run tests multiple times to catch flakiness.
    - Check coverage increased appropriately.
    - Ensure tests are meaningful, not just coverage.
2. Use browser automation tools via MCP for end-to-end validation:
    - Test critical user journeys.
    - Verify UI behavior matches expectations.
3. Document testing decisions:
    - Update test documentation if needed.
    - Add comments for complex test setups.
    - Create scratchpad for testing strategies.

## Report

Document and communicate test results:

1. Summarize test improvements in a scratchpad.
2. If part of a PR, update the PR description with test details.
3. Commit all changes with descriptive messages.

Remember that good tests are fast, reliable, and clearly communicate intent.