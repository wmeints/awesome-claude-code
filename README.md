# Awesome Claude Code

A collection of reusable agents and skills for [Claude
Code](https://docs.anthropic.com/en/docs/claude-code).

> **Important:** Everything in this repository is optional. You should review
> the contents of any agent or skill before adding it to your project. These are
> starting points — adapt them to fit your team's workflow, conventions, and
> tooling.

## What's in here?

### Agents

Agents are custom personas you can invoke in Claude Code to perform specialized
tasks. Copy an agent file into your project's `.claude/agents/` directory to use
it.

### Skills

Skills are reusable prompt templates that Claude Code can invoke via slash
commands. Copy a skill folder into your project's `.claude/skills/` directory to
use it.

#### [Grill-me](.claude/skills/grill-me/SKILL.md)

This is a skill I adopted from Matt Pocock. It is a universal skill that can be
helpful when you're exploring a topic in your code base or putting together a
plan. When you use this skill, Claude Code will interview you and help you
create shared understanding between you and the agent. This is of course not a
stand-in for real human understanding as Claude Code is only a machine. But it
can be helpful still. I use this to explore new ideas before presenting them to
anybody. It also helps me refine a backlog and work on prototypes.

#### [Create-PRD](.claude/skills/create-prd/SKILL.md)

This is another skill I picked up from Matt Pocock. When designing an initial
version of a new project I like to use this skill to put together a breakdown of
what I'm trying to solve. The workflow here is simple: I ask Claude to grill me
first on the topic to create the shared understanding between me and the AI.
Then I use the `/create-prd` skill to turn the transcript of the conversation
into a PRD. Then, I use the PRD to build other things like proper architecture
documentation.

The output of the skill is stored in
`docs/product/<number>-<description-title>.md`. You can create multiple PRDs in
case you're working in multiple phases.
