# 🧠 Claude Code Best Practices

A practical guide to using Claude Code, Anthropic’s agentic coding assistant, effectively in real-world development workflows. This repo distills best practices, patterns, and examples for integrating Claude Code into your terminal-based coding environment.

## ✨ What is Claude Code?

Claude Code is a command-line tool that gives you direct access to Claude’s reasoning and coding capabilities. It’s designed for agentic coding - where Claude autonomously explores, edits, and explains code across your project. Think of it as a collaborative AI pair programmer that understands your repo structure, coding conventions, and workflows.

## 📦 What You’ll Find Here

- 🛠️ Setup Tips
    - How to configure your environment for Claude Code 
- 🧠 Prompt Design & Context Handling
    - Effective ways to ask Claude for code generation, refactoring, or debugging
    - Using `CLAUDE.md` to preload project context   
- 🧪 Testing & Debugging
    - Run tests, fix failures, and lint code—all from the CLI
- 🔄 Git Workflows
    - Create commits, open PRs, and resolve merge conflicts with Claude
- ⚙️ Hooks & Automation
    - Enforce naming conventions, testing protocols, and architectural rules
- 🛡️ Safety & Control
    - How Claude Code handles read-only access and tool permissions
    - Works with your tools, your standards, your repo
- 🧰 Real Examples
    - Scripts and terminal sessions showing Claude Code in action

## 🧭 Why Use Claude Code?

Claude Code is optimized for agentic coding - AI that acts with autonomy and awareness:

- Understands your codebase structure and dependencies
- Makes coordinated edits across files
- Integrates with GitHub, GitLab, VS Code, and JetBrains IDEs
- Designed for flexibility, transparency, and developer control

## 🔧 Custom Slash Commands

This repository includes a collection of custom slash commands designed to streamline development workflows with Claude Code. Use `/help-commands` to get detailed information about all available commands.

### Project Management & Documentation

- [`/custom-init`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/commands/custom-init.md)  
  Automatically generates comprehensive CLAUDE.md files for any project by analyzing project structure, technology stack, and development patterns.

- [`/help-commands`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/commands/help-commands.md)  
  Provides comprehensive help documentation for all available custom commands, including usage examples and best practices.

### Version Control & Git

- [`/commit`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/commands/commit.md)  
  Creates well-formatted conventional commits following best practices with automatic staging, diff analysis, and atomic commit recommendations. Uses standardized commit templates from [`.gitmessage`](https://github.com/awattar/claude-code-best-practices/blob/main/.gitmessage) and [`.github/COMMIT_CONVENTION.md`](https://github.com/awattar/claude-code-best-practices/blob/main/.github/COMMIT_CONVENTION.md).

- [`/issue`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/commands/issue.md)  
  End-to-end GitHub issue resolution following GitHub Flow with automated planning, branch creation, and incremental implementation. Integrates with GitHub PR templates from [`.github/pull_request_template.md`](https://github.com/awattar/claude-code-best-practices/blob/main/.github/pull_request_template.md).

- [`/reviewpr`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/commands/reviewpr.md)  
  Comprehensive pull request review process with CI/CD checks, code quality analysis, and structured feedback via GitHub CLI.

### Code Analysis & Testing

- [`/test`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/commands/test.md)  
  Comprehensive test execution and improvement with framework detection, targeted test runs, coverage analysis, and automated fixes.


## 🤖 Specialized AI Agents

This repository includes a collection of 10 specialized AI agents that provide domain-specific expertise across all development workflows. These agents work automatically with commands to deliver expert-level capabilities in architecture, development, and quality assurance.

> **Note:** Commands also leverage Claude Code's built-in [`general-purpose`](https://docs.anthropic.com/en/docs/claude-code/sub-agents) agent for complex multi-step analysis and file searching. It ships with Claude Code, so it is not defined in this repository.

### 🏗️ Core Infrastructure Agents

- [`general-solution-architect`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/agents/general-solution-architect.md)  
  Architecture analysis, technology stack decisions, scalability planning, and distributed systems design.

- [`general-technical-writer`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/agents/general-technical-writer.md)  
  Documentation creation, API documentation, formatting, and technical content organization.

- [`general-pm`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/agents/general-pm.md)  
  Product management oversight — issue creation, prioritization, progress tracking, and lifecycle management.

### 💻 Development Specialists

- [`general-fullstack-developer`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/agents/general-fullstack-developer.md)  
  End-to-end feature implementation spanning database, API, and frontend layers with seamless integration.

- [`general-backend-developer`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/agents/general-backend-developer.md)  
  API development, database design, server-side logic, and backend performance optimization.

- [`general-frontend-developer`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/agents/general-frontend-developer.md)  
  UI/UX implementation, component patterns, browser automation, and modern JavaScript frameworks.

- [`general-devops`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/agents/general-devops.md)  
  Infrastructure automation, CI/CD pipeline design, container orchestration, and reliability engineering.

### 🛡️ Quality Assurance & Leadership

- [`general-qa`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/agents/general-qa.md)  
  Testing strategies, test automation, comprehensive validation, and quality assurance methodologies.

- [`general-code-quality-debugger`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/agents/general-code-quality-debugger.md)  
  Code review, systematic debugging, refactoring guidance, and technical debt reduction.

- [`general-technical-project-lead`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/agents/general-technical-project-lead.md)  
  Security assessments, strategic technical decisions, performance optimization, and architectural leadership.

**Agent Integration:** These specialized agents work seamlessly with all custom commands, automatically providing domain expertise when needed. Commands like `/issue`, `/reviewpr`, and `/test` leverage multiple agents to deliver comprehensive, expert-level results.


## 🧩 Skills

Skills are model-invoked capabilities: instead of being triggered by a slash command, Claude Code loads them **automatically** when the task matches the skill's `description`. Each skill lives in `.claude/skills/<name>/SKILL.md` with YAML frontmatter (`name`, `description`) and instructions in the body.

This repository includes one example:

- [`conventional-commits`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/skills/conventional-commits/SKILL.md)  
  Automatically enforces the project's commit format whenever a commit message is being authored — no command needed.

**Skills vs. commands vs. agents:**

| Mechanism | Trigger | Best for |
|-----------|---------|----------|
| **Slash command** | User types `/name` | Explicit, on-demand workflows |
| **Skill** | Claude matches the `description` | Conventions and know-how that should apply automatically |
| **Subagent** | Delegated by Claude or a command | Heavy, focused work that should run in its own context window so it doesn't crowd the main session |

See the [Skills documentation](https://docs.anthropic.com/en/docs/claude-code/skills) for authoring details, including bundling scripts and reference files alongside `SKILL.md`.


## ⚙️ Project Configuration

The repository ships a checked-in [`.claude/settings.json`](https://github.com/awattar/claude-code-best-practices/blob/main/.claude/settings.json) that demonstrates two of the most useful project-level configuration mechanisms:

### Permissions

Scoped `allow` / `ask` / `deny` rules let Claude Code run safe, routine commands (`git status`, `gh pr view`, etc.) without prompting, require confirmation for riskier ones (`git push`), and block reads of sensitive files (`.env`, `secrets/`). Tune these to your team's risk tolerance — settings are merged from user, project, and local scopes.

### Hooks

Hooks register shell commands that run automatically on lifecycle events (`PreToolUse`, `PostToolUse`, `Stop`, etc.). The bundled example uses a `Stop` hook to print `git status --short` at the end of every turn so you always see what changed. Other common patterns:

- **`PostToolUse`** matching `Edit|Write` — auto-format or lint files after Claude edits them.
- **`PreToolUse`** matching `Bash` — block dangerous commands before they execute.
- **`Stop`** — send a desktop/Slack notification when Claude finishes a long task.

See the [Hooks documentation](https://docs.anthropic.com/en/docs/claude-code/hooks) for the full event list and JSON schema.


## 📚 Claude Code Documentation

- [`Models Overview`](https://docs.anthropic.com/en/docs/about-claude/models/overview)  
  _"Claude is a family of state-of-the-art large language models developed by Anthropic. This guide introduces our models and compares their performance with legacy models."_
- [`Best Practices for Agentic Coding`](https://www.anthropic.com/engineering/claude-code-best-practices)  
  _"Claude Code is a command line tool for agentic coding. This post covers tips and tricks that have proven effective for using Claude Code across various codebases, languages, and environments."_
- [`Common Workflows`](https://docs.anthropic.com/en/docs/claude-code/common-workflows)  
  _"Learn about common workflows with Claude Code. Each task in this document includes clear instructions, example commands, and best practices to help you get the most from Claude Code."_
    - [`Run Parallel Claude Code Sessions with Git Worktrees`](https://docs.anthropic.com/en/docs/claude-code/common-workflows#run-parallel-claude-code-sessions-with-git-worktrees)  
      _"Suppose you need to work on multiple tasks simultaneously with complete code isolation between Claude Code instances."_
- [`Manage Claude's Memory`](https://docs.anthropic.com/en/docs/claude-code/memory)  
  _"Learn how to manage Claude Code’s memory across sessions with different memory locations and best practices. Claude Code can remember your preferences across sessions, like style guidelines and common commands in your workflow."_
- [`Hooks`](https://docs.anthropic.com/en/docs/claude-code/hooks)  
  _"Customize and extend Claude Code’s behavior by registering shell commands."_
- [`Sub-agents`](https://docs.anthropic.com/en/docs/claude-code/sub-agents)  
  _"Create and use specialized AI sub agents in Claude Code for task-specific workflows and improved context management."_
    - [`Claude Code Subagents Collection`](https://github.com/davepoon/claude-code-subagents-collection) by [davepoon](https://github.com/davepoon)  
      _"A comprehensive collection of specialized AI subagents for Claude Code, designed to enhance development workflows with domain-specific expertise."_
- [`GitHub Actions`](https://docs.anthropic.com/en/docs/claude-code/github-actions)  
  _"Learn about integrating Claude Code into your development workflow with Claude Code GitHub Actions. Claude Code GitHub Actions brings AI-powered automation to your GitHub workflow. With a simple @claude mention in any PR or issue, Claude can analyze your code, create pull requests, implement features, and fix bugs - all while following your project's standards."_

### 🔖 Other Documentation

- [`My Claude Code Workflow and Personal Tips`](https://thegroundtruth.substack.com/p/my-claude-code-workflow-and-personal-tips) by [paradite](https://github.com/paradite)  
  _"How I use roadmap + task files to manage Claude Code, and my personal tips for effective Claude Code usage."_
- [`Playwright MCP Server`](https://github.com/microsoft/playwright-mcp)
  _"A Model Context Protocol server that provides browser automation capabilities using Playwright. It lets Claude interact with web pages, fill forms, take screenshots, and run end-to-end checks against a real browser. The older Puppeteer MCP server is archived — Playwright MCP is the maintained replacement."_

## 💡 Inspired by:

- [`The Claude Code WORKFLOW with GitHub to Build Complex Apps`](https://www.youtube.com/watch?v=FjHtZnjNEBU) by [gregbaugues](https://github.com/gregbaugues)  
  _"f you're struggling to build an app with Claude Code, it's probably because you need a better process. Writing code is only one part of shipping complex software. Thankfully, we have a workflow to help us build complex software, and it works great with Claude Code."_
- [`How to Give Claude Code a Better "Memory" of Your Project`](https://www.youtube.com/watch?v=higAxJk_zig) by [iannuttall](https://github.com/iannuttall)  
  _"In this video I show you a set of custom slash commands I built that will help you to log all of the changes you make with Claude Code into a simple memory system that is so much better than using /compact."_
- [`Claude Code Multitasking Made EASY`](https://www.youtube.com/watch?v=Bz5fyyCa2-0) by [CasJam](https://github.com/CasJam)  
  _"This video shows you how to use Git Worktrees and my method for automating the workflow for spinning up new worktrees to run multiple Claude Code agents simultaneously."_
- [`Claude Code Hooks is AMAZING: "Text Message Me When AI Agent is Done"`](https://www.youtube.com/watch?v=bvwn3h2XUp4) by [AllAboutAI-YT](https://github.com/AllAboutAI-YT)  
  _A hands-on demo showing how to use Claude Code hooks to send a text message when your AI coding agent finishes a task—automating notifications with shell commands._
- [`My Claude Code Sub Agents BUILD THEMSELVES`](https://www.youtube.com/watch?v=7B2HJr0Y68g) by [disler](https://github.com/disler)  
  _"Are you using Claude Code Sub Agents the WRONG way? I have a BIG IDEA for you. Sub Agents just changed EVERYTHING about AI coding. With the right approach, your agents can now BUILD THEMSELVES."_

## 🔗 Related:

- [`Awesome Claude Code`](https://github.com/hesreallyhim/awesome-claude-code) by [hesreallyhim](https://github.com/hesreallyhim)  
  _"This is a curated list of slash-commands, CLAUDE.md files, CLI tools, and other resources and guides for enhancing your Claude Code workflow, productivity, and vibes."_
- [`SuperClaude Framework`](https://github.com/SuperClaude-Org/SuperClaude_Framework) by [SuperClaude-Org](https://github.com/SuperClaude-Org)  
  _"A framework that extends Claude Code with specialized commands, personas, and MCP server integration."_
- [`Agent OS`](https://github.com/buildermethods/agent-os) by [buildermethods](https://github.com/buildermethods)  
  _"Agent OS transforms AI coding agents from confused interns into productive developers."_
