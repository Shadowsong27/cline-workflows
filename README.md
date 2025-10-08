# Cline Workflows

A collection of AI-powered workflows for specification-driven software development with Cline. These workflows help automate and streamline common development tasks from planning to code review.

## Overview

This repository contains reusable workflow templates that can be used with Cline (formerly Claude Dev) to enhance your development process. Each workflow is designed to guide Cline through specific tasks with clear instructions and best practices.

## Available Workflows

### 1. Task Initialization (`init-task.md`)
**Purpose**: Transform free-form ideas into formal Technical Planning Documents

**What it does**:
- Parses high-level task descriptions
- Extracts key information (problem, goals, scope, technical approach)
- Generates a structured planning document in Markdown
- Identifies gaps and asks clarifying questions
- Iterates until a complete plan is ready

**Output**: Creates `.clinespecs/<task-name>/task_brief.md` with:
- Background and problem statement
- Goals and success criteria
- Scope definition (in/out of scope)
- Proposed technical solution
- Risks and dependencies
- Open questions

### 2. Task Breakdown (`breakdown-task.md`)
**Purpose**: Convert task briefs into detailed, executable implementation plans

**What it does**:
- Reads the task brief from `.clinespecs/<task-name>/task_brief.md`
- Extracts and summarizes key information
- Decomposes high-level plans into concrete technical steps
- Identifies ambiguities and dependencies
- Creates a sequential checklist for implementation

**Output**: Creates `.clinespecs/<task-name>/task_breakdown.md` with:
- Ticket title and user story
- Technical description
- Acceptance criteria
- Detailed technical task checklist
- Questions and ambiguities
- Dependencies

### 3. Git Commit (`git-commit.md`)
**Purpose**: Intelligently stage and commit changes with automated analysis

**What it does**:
- Analyzes all repository changes (staged, unstaged, untracked)
- Applies heuristics to identify safe files to stage
- Automatically stages appropriate files
- Reports staging decisions with justification
- Generates conventional commit messages
- Requests user approval before committing

**Key Features**:
- Automatic detection of sensitive files (credentials, secrets)
- Filters out debug code and temporary files
- Excludes large files and build artifacts
- Generates Conventional Commits format messages
- Single approval checkpoint for efficiency

### 4. PR Review (`pr-review.md`)
**Purpose**: Conduct thorough GitHub Pull Request reviews using the `gh` CLI

**What it does**:
- Gathers PR information (title, description, diff, files)
- Examines context by reading original files
- Analyzes changes for quality, bugs, performance, and security
- Provides detailed assessment with justification
- Asks for user confirmation before submitting review
- Optionally drafts review comments

**Key Features**:
- Comprehensive code analysis
- Context-aware review process
- Friendly, humble communication style
- Support for inline code comments
- Proper multi-line comment formatting

## Usage

### Setting Up Workflows

1. **Clone this repository** or copy individual workflow files
2. **Reference workflows in Cline** by providing the workflow content when starting a task
3. **Trigger workflows** by describing your intent (e.g., "Help me plan a new feature" or "Review this PR")

### Example Usage

#### Planning a New Feature
```
User: "I need to add JWT authentication to our API"
Cline: [Uses init-task.md workflow to create a planning document]
```

#### Breaking Down a Task
```
User: "Break down the JWT authentication task"
Cline: [Uses breakdown-task.md to create implementation steps]
```

#### Committing Changes
```
User: "Commit my changes"
Cline: [Uses git-commit.md to analyze, stage, and commit]
```

#### Reviewing a PR
```
User: "Review PR #123"
Cline: [Uses pr-review.md to analyze and review the PR]
```

## Workflow Structure

Each workflow follows a consistent pattern:

1. **Clear Objective**: Defines what the workflow accomplishes
2. **Detailed Steps**: Sequential instructions for Cline to follow
3. **Templates**: Structured output formats (usually Markdown)
4. **Examples**: Real-world usage demonstrations
5. **Guidelines**: Best practices and communication patterns

## Integration with Cline

These workflows are designed to work seamlessly with Cline's capabilities:

- **File Operations**: Reading, writing, and searching files
- **Command Execution**: Running git, gh, and other CLI tools
- **Interactive Prompts**: Asking clarifying questions when needed
- **Sequential Thinking**: Using MCP sequential thinking for complex reasoning
- **Context Awareness**: Leveraging project structure and history

## Best Practices

### For Task Planning
- Start with high-level goals, iterate to add detail
- Explicitly define what's out of scope
- Document risks and dependencies early
- Keep plans focused and actionable

### For Implementation
- Break tasks into small, sequential steps
- Each step should be clear and verifiable
- Document ambiguities before starting
- Update plans as you learn more

### For Git Commits
- Let the workflow handle staging decisions
- Review the generated commit message
- Trust the heuristics for common cases
- Manually handle edge cases when needed

### For PR Reviews
- Examine context before judging changes
- Be thorough but friendly in feedback
- Request changes when needed, don't just approve
- Use inline comments for specific code issues

## Contributing

Contributions are welcome! When adding new workflows:

1. Follow the existing structure and format
2. Include detailed step-by-step instructions
3. Provide clear examples
4. Document the output format
5. Test with real-world scenarios

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Related Resources

- [Cline Documentation](https://docs.cline.bot)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [GitHub CLI Documentation](https://cli.github.com/manual/)

## Support

For issues or questions:
- Open an issue in this repository
- Refer to individual workflow files for detailed instructions
- Check Cline documentation for general usage help
