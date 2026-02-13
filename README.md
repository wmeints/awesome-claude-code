# Awesome Claude Code

A collection of reusable agents and skills for [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

> **Important:** Everything in this repository is optional. You should review
> the contents of any agent or skill before adding it to your project. These are
> starting points — adapt them to fit your team's workflow, conventions, and
> tooling.

## What's in here?

### Agents

Agents are custom personas you can invoke in Claude Code to perform specialized
tasks. Copy an agent file into your project's `.claude/agents/` directory to use
it.

| Agent                     | File                              | Description                                                                                                                                                                                                     |
| ------------------------- | --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Architecture Reviewer** | `agents/architecture-reviewer.md` | Reviews architecture documentation (arc42 format) for completeness, ADR quality, quality goal coverage, and alignment with product goals. Produces a structured review report with prioritized recommendations. |

### Skills

Skills are reusable prompt templates that Claude Code can invoke via slash commands. Copy a skill folder into your project's `.claude/skills/` directory to use it.

| Skill                 | Folder                      | Description                                                                                                                                                                                                                                               |
| --------------------- | --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Storybook Testing** | `skills/storybook-testing/` | Creates or modifies Storybook component stories and tests. Includes a template for `@storybook/nextjs-vite` stories.                                                                                                                                      |
| **Record ADR**        | `skills/record-adr/`        | Guides you through writing Architecture Decision Records with proper context, alternatives, pros/cons, and consequences. Includes an ADR template.                                                                                                        |
| **Feature Spec**      | `skills/spec/`              | Interactive feature specification writer. Walks you through problem discovery, user stories, functional requirements, acceptance scenarios (Given/When/Then), domain modeling, and non-functional requirements. Produces a complete spec from a template. |
| **Test Review**       | `skills/test-review/`       | Reviews test code for coverage adequacy, redundancy, AAA pattern compliance, assertion quality, single responsibility, and fixture usage. Includes a self-critique step to filter out noise.                                                              |

## How to use

### Prerequisites

You need [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed and configured.

### Installing an agent

1. Copy the agent's `.md` file into your project's `.claude/agents/` directory:
   ```
   .claude/
     agents/
       architecture-reviewer.md
   ```
2. Open Claude Code in your project and invoke the agent by name — e.g., ask Claude to run the architecture reviewer.

### Installing a skill

1. Copy the skill's entire folder into your project's `.claude/skills/` directory:
   ```
   .claude/
     skills/
       record-adr/
         SKILL.md
         templates/
           adr.md
   ```
2. In Claude Code, invoke the skill with its name — e.g., `/record-adr`.

### Adapting to your project

Most of these agents and skills were written with specific project conventions in mind (arc42 documentation, Next.js + Storybook, pytest, etc.). Before using them:

- **Read the full source.** Understand what the agent or skill does and what assumptions it makes.
- **Edit paths and conventions** to match your project structure. For example, the ADR skill stores files in `docs/architecture/adr/` — change this if your project uses a different location.
- **Remove or modify sections** that don't apply. The architecture reviewer references specific quality goals that won't match your project.
- **Adjust tooling references.** The storybook testing skill targets `@storybook/nextjs-vite` — swap this for your framework's Storybook adapter.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
