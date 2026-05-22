---
description: Generate a comprehensive CLAUDE.md by analyzing the current project
---

# Claude Code User Command: Custom Init

This command helps you initialize a new, well-formatted CLAUDE.md file with codebase documentation.

## Usage

To initialize a new CLAUDE.md file with codebase documentation, just type:

```
/custom-init
```

## Relationship to native `/init`

Claude Code ships with a built-in `/init` command that also generates a `CLAUDE.md`.
`/custom-init` covers the same goal through the explicit, deterministic phased workflow
below, which produces a more structured result: staged analysis, per-feature detection,
a versioned technology stack inventory, and consistent section ordering. Pick whichever
fits the project — they are alternatives, not a hierarchy.

## What This Command Does

Analyzes the project's architecture, technology stack, and key features through the phased workflow below, then writes the findings to `CLAUDE.md` so Claude (or any AI assistant) can work effectively in the codebase.

## Agents Used

The main session orchestrates and dispatches each pass to the **best-fit specialist agent** through the Task tool, so each agent works in its own context window. Reach for **general-purpose** only as a fallback when no specialist matches a pass.

- **general-solution-architect** — Phase 2 (architecture + technology stack).
- **general-backend-developer** — Phase 3 backend passes (authentication, business domain, data access, communication).
- **general-devops** — Phase 3 infrastructure pass and Phase 4 deployment pass.
- **general-qa** — Phase 4 testing pass.
- **general-code-quality-debugger** — Phase 4 troubleshooting pass.
- **general-technical-writer** — Phase 4 documentation-discovery pass and Phase 5 assembly.

Phases 0 and 1 run inline in the main session. Phases 2, 3, and 4 can all be dispatched in the same message and run concurrently. Phase 5 is sequential — it consumes the outputs of Phases 2–4 and must wait for them to return.

Follow these steps:

## Phase 0: Initialization

1. **Command Execution**
   - Execute the command in the current directory.
   - Validate that the current directory is a project root.
   - Check for an existing CLAUDE.md file.
   - Set the analysis depth to a comprehensive scan.
2. **Environment Setup**
   - Verify the current directory contains project files.
   - Check for a `.git` directory or other VCS metadata.
   - Confirm read access to project files.
3. **Tool Detection**
   - Check which relevant CLI tools are available (`git`, `docker`, `npm`, `dotnet`, etc.).
   - Note language-specific tooling that can inform deeper analysis.
4. **Configuration Loading**
   - Use smart defaults for all settings.
   - Respect ignore patterns from `.gitignore`.
   - Apply standard markdown output formatting.
5. **Pre-flight Checks**

   ```
   Initializing CLAUDE.md generation...
   ✅ Project root detected: /path/to/project
   ✅ Project type: ASP.NET Core 8.0
   ✅ Existing CLAUDE.md: Not found (will create)
   ✅ Analysis mode: comprehensive
   ✅ Available tools: git, dotnet, docker
   ➡️ Starting analysis...
   ```

## Phase 1: Project Discovery

- Detect the project type from build files (`package.json`, `*.csproj`, `pom.xml`, `pyproject.toml`, `go.mod`, etc.).
- Identify the primary language and framework.
- Scan the directory structure for architecture patterns.
- Find existing documentation (`README.md`, `docs/`).

## Phase 2: Core Section Generation

1. **Overview & Quick Start**
   - Extract the project description from the README or package metadata.
   - Detect prerequisites from dependency files.
   - Generate setup commands based on the project type.
   - Create verification steps.
2. **Architecture Analysis**
   - Map the folder structure to known patterns (MVC, DDD, Clean, etc.).
   - Identify architectural layers and boundaries.
   - Find design pattern implementations.
   - Extract architecture decisions from existing docs.
3. **Technology Stack**
   - Parse all dependency files for exact versions.
   - Categorize into languages, frameworks, libraries, and tools.
   - Distinguish development from production dependencies.
   - Detect infrastructure services from `docker-compose.yml` and k8s files.
4. **Development Section**
   - Extract build commands from scripts and configs.
   - Generate run commands for different environments.
   - Map key files by analyzing imports and references.
   - Document common workflows from scripts or docs.

## Phase 3: Feature Analysis (parallel specialist fan-out)

Dispatch one specialist subagent per pass in a single message so they run in parallel. Each pass searches the codebase for one category of patterns and returns a structured summary that Phase 5 will assemble. The matching specialist is noted per pass:

1. **Authentication** — general-backend-developer
   - Search patterns: auth middleware, login routes, token handling.
   - Config locations: startup files, auth configs, environment vars.
   - Output: mechanism, provider, endpoints, default credentials.
2. **Business Domain** — general-backend-developer
   - Search patterns: entity classes, aggregates, services, DTOs.
   - Analyze: inheritance hierarchies, business rule locations.
   - Output: core entities, domain services, use cases.
3. **Data Access** — general-backend-developer
   - Search patterns: DbContext, repositories, migrations, SQL files.
   - Config: connection strings, ORM configuration.
   - Output: database tech, patterns, migration commands.
4. **Communication** — general-backend-developer
   - Search patterns: controllers, API routes, message handlers.
   - External: service clients, integration configs.
   - Output: API structure, integrations, messaging.
5. **Infrastructure** — general-devops
   - Parse: `docker-compose.yml`, k8s manifests, Terraform files.
   - Extract: service names, ports, dependencies.
   - Output: service map with ports and connections.

## Phase 4: Additional Sections (parallel specialist fan-out)

Same dispatch pattern as Phase 3 — one specialist subagent per pass, all sent in a single message so they run in parallel:

1. **Testing Analysis** — general-qa
   - Detect test frameworks from imports and configs.
   - Count test files by type (unit, integration, e2e).
   - Extract test commands from scripts.
   - Find test data and fixture locations.
2. **Deployment Analysis** — general-devops
   - Check for CI/CD files (`.github/workflows`, `.gitlab-ci.yml`).
   - Find deployment scripts and configs.
   - Extract environment-specific settings.
   - Document deployment commands.
3. **Troubleshooting Scan** — general-code-quality-debugger
   - Search for `TODO`, `FIXME`, `HACK`, `BUG` comments.
   - Check for workaround patterns.
   - Extract content from `KNOWN_ISSUES.md` or similar.
   - Find common error-handling patterns.
4. **Documentation Discovery** — general-technical-writer
   - Locate API docs (Swagger, OpenAPI).
   - Find additional markdown files.
   - Check for inline documentation patterns.
   - List external documentation links.

## Phase 5: Content Assembly

1. **Structure Assembly**
   - Combine the outputs from all analysis passes.
   - Apply consistent markdown formatting.
   - Order sections by priority (must-have ➡️ nice-to-have).
   - Add navigation links between sections.
2. **Quality Checks**
   - Ensure all commands are executable.
   - Verify file paths are correct.
   - Check for missing critical sections.
   - Validate markdown syntax.
3. **File Generation**
   - Create CLAUDE.md in the project root.
   - If the file exists, back it up as `CLAUDE.md.backup` and reuse any still-accurate content.
   - Write the comprehensive documentation.
   - Report generation completion.

## Example Orchestration

This is one representative run. Agent assignment adapts to what the project actually
contains — a frontend-only app has no data-access pass, a library has no deployment
pass, and so on. Skip passes that don't apply, and fall back to **general-purpose**
for anything without a clear specialist.

```
Main session (orchestrator)
│
├── Phase 0: Initialization              — inline
├── Phase 1: Project Discovery           — inline
│
├── ─── dispatched in one message, run in parallel ───
│   ├── Phase 2: Core Section Generation  — general-solution-architect
│   ├── Phase 3: Feature Analysis
│   │   ├── Authentication                — general-backend-developer
│   │   ├── Business Domain               — general-backend-developer
│   │   ├── Data Access                   — general-backend-developer
│   │   ├── Communication                 — general-backend-developer
│   │   └── Infrastructure                — general-devops
│   └── Phase 4: Additional Sections
│       ├── Testing                       — general-qa
│       ├── Deployment                    — general-devops
│       ├── Troubleshooting               — general-code-quality-debugger
│       └── Documentation                 — general-technical-writer
│
└── Phase 5: Content Assembly            — general-technical-writer
                                           (waits for Phases 2–4 to return)
```

## Best Practices

- Keep CLAUDE.md accurate — stale context is worse than no context. Re-run `/custom-init` or hand-edit when the architecture or tooling changes.
- Reference shared templates with the `@` prefix (e.g. `@.gitmessage`) instead of duplicating their content.
- Be concise: document what is non-obvious, not what Claude can already read from the code.
