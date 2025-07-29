# Claude Code User Command: Custom Init

This command helps you initialize a new, well-formatted CLAUDE.md file with codebase documentation.

## Usage

To initialize a new CLAUDE.md file with codebase documentation, just type:

```
/custom-init
```

## What This Command Does

1. This command analyzes a software project and generates a comprehensive CLAUDE.md file that serves as a guide for Claude (or any AI assistant) when working with the codebase.
2. It automatically detects the project's architecture, technology stack, key features, and development patterns, then documents them in a structured format.
3. The generated file helps Claude understand the project context, locate important files, run correct commands, and follow established patterns when assisting with development tasks.

## Agents Used

This command leverages three specialized agents for optimal results:

- **general-solution-architect** - For analyzing project architecture patterns and technology stack decisions
- **general-technical-writer** - For creating comprehensive, well-structured documentation
- **general-purpose** - For complex multi-step analysis and file searching across large codebases

Each agent contributes specialized expertise to ensure thorough project analysis and high-quality documentation generation.

Follow these steps:

## Phase 0: Initialization

1. **Command Execution**
   - Execute command in current directory.
   - Validate current directory is a project root.
   - Check for existing CLAUDE.md file.
   - Set analysis depth to comprehensive scan.
2. **Environment Setup**
   - Verify current directory contains project files.
   - Check for .git directory or other VCS.
   - Ensure read permissions for project files.
   - Create temporary workspace for analysis.
3. **Tool Detection**
   - Check available system commands (git, docker, npm, dotnet, etc.).
   - Verify language-specific tools for deeper analysis.
   - Set up file parsing utilities.
   - Initialize pattern matching engines.
4. **Configuration Loading**
   - Use smart defaults for all settings.
   - Set up ignore patterns from .gitignore.
   - Configure standard output formatting.
   - Prepare comprehensive analysis mode.
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

## Phase 1: Project Analysis

1. **Project Discovery**
   - Detect project type from build files (package.json, .csproj, pom.xml, etc.).
   - Identify primary language and framework.
   - Scan directory structure for architecture patterns.
   - Find existing documentation (README.md, docs/).

## Phase 2: Core Section Generation

1. **Overview & Quick Start**
   - Extract project description from README or package metadata.
   - Detect prerequisites from dependency files.
   - Generate setup commands based on project type.
   - Create verification steps.
2. **Architecture Analysis**
   - Map folder structure to known patterns (MVC, DDD, Clean, etc.).
   - Identify architectural layers and boundaries.
   - Find design pattern implementations.
   - Extract architecture decisions from docs.
3. **Technology Stack**
   - Parse all dependency files for exact versions.
   - Categorize into languages, frameworks, libraries, tools.
   - Identify development vs production dependencies.
   - Detect infrastructure services from docker-compose, k8s files.
4. **Development Section**
   - Extract build commands from scripts and configs.
   - Generate run commands for different environments.
   - Map key files by analyzing imports and references.
   - Document common workflows from scripts or docs.

## Phase 3: Feature Analysis (Sub-Agent Approach)

Each feature sub-agent specializes in detecting patterns:

1. **Authentication Agent**
   - Search patterns: Auth middleware, login routes, token handling.
   - Config locations: Startup files, auth configs, environment vars.
   - Output: Mechanism, provider, endpoints, default credentials.
2. **Business Domain Agent**
   - Search patterns: Entity classes, aggregates, services, DTOs.
   - Analyze: Inheritance hierarchies, business rule locations.
   - Output: Core entities, domain services, use cases.
3. **Data Access Agent**
   - Search patterns: DbContext, repositories, migrations, SQL files.
   - Config: Connection strings, ORM configuration.
   - Output: Database tech, patterns, migration commands.
4. **Communication Agent**
   - Search patterns: Controllers, API routes, message handlers.
   - External: Service clients, integration configs.
   - Output: API structure, integrations, messaging.
5. **Infrastructure Agent**
   - Parse: docker-compose.yml, k8s manifests, terraform files.
   - Extract: Service names, ports, dependencies.
   - Output: Service map with ports and connections.

## Phase 4: Additional Sections

1. **Testing Analysis**
   - Detect test frameworks from imports and configs.
   - Count test files by type (unit, integration, e2e).
   - Extract test commands from scripts.
   - Find test data and fixture locations.
2. **Deployment Analysis**
   - Check for CI/CD files (.github/workflows, .gitlab-ci.yml).
   - Find deployment scripts and configs.
   - Extract environment-specific settings.
   - Document deployment commands.
3. **Troubleshooting Scan**
   - Search for TODO, FIXME, HACK, BUG comments.
   - Check for workaround patterns.
   - Extract from KNOWN_ISSUES.md or similar.
   - Find common error handling patterns.
4. **Documentation Discovery**
   - Locate API docs (Swagger, OpenAPI).
   - Find additional markdown files.
   - Check for inline documentation patterns.
   - List external documentation links.

## Phase 5: Content Assembly

1. **Structure Assembly**
   - Combine outputs from all agents.
   - Apply consistent markdown formatting.
   - Order sections by priority (must-have ➡️ nice-to-have).
   - Add navigation links between sections.
2. **Quality Checks**
   - Ensure all commands are executable.
   - Verify file paths are correct.
   - Check for missing critical sections.
   - Validate markdown syntax.
3. **File Generation**
   - Create CLAUDE.md in project root.
   - If file exists, backup as CLAUDE.md.backup.
   - Write comprehensive documentation.
   - Report generation completion.

## Example Agent Coordination

```
Main Command
├── Project Analyzer
│   └── Detects project type and structure
├── Core Agents (Sequential)
│   ├── Overview Agent
│   ├── Architecture Agent
│   ├── Tech Stack Agent
│   └── Development Agent
├── Feature Agents (Parallel)
│   ├── Authentication Agent
│   ├── Domain Agent
│   ├── Data Access Agent
│   ├── Communication Agent
│   └── Infrastructure Agent
├── Additional Agents (Parallel)
│   ├── Testing Agent
│   ├── Deployment Agent
│   ├── Troubleshooting Agent
│   └── Documentation Agent
└── Assembly Agent
    └── Combines all outputs into final CLAUDE.md
```

## Implementation Priority

1. **Phase 1**: Core section detection and generation.
2. **Phase 2**: Feature analysis with pattern recognition.
3. **Phase 3**: Smart defaults and comprehensive templates.
4. **Phase 4**: Quality validation and error handling.
5. **Phase 5**: Performance optimization for large projects.