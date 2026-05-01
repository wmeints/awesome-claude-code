# Awesome Claude Code

A collection of reusable agents and skills for [Claude
Code](https://docs.anthropic.com/en/docs/claude-code).

> **Important:** Everything in this repository is optional. You should review
> the contents of any agent or skill before adding it to your project. These are
> starting points — adapt them to fit your team's workflow, conventions, and
> tooling.

## What's in here?

### Skills

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

#### [create-backlog](.claude/skills/create-backlog/SKILL.md)

I use this skill to turn a set of requirements into actionable issues. I prefer
to implement vertical slices. I first tried to work with horizontal layers, but
it requires the agent to explore the codebase multiple teams. It's more
expensive and often leads to very complicated results. Vertical slicing is much
nicer, because the agent can look at things that are consistent together.

All issues created are marked with the `needs-triage` label to make sure you can
easily find them and review them in your favorite source control environment.

## Installation

Use the following command to install the skills:

```bash
npx skills install wmeints/awesome-claude-code
```

The tool will ask you where you want to put the contents of this repo. Choose
whatever makes you feel happy :-)

## Background information

I frequently work with teams on all sorts of software and people ask me, what do you do to stay productive with AI?
Well, there are many angles you can take here. But my workflow generally looks as described below.

### Workflow steps

I like to take the following approach when designing something bigger:

1. Discuss a product slice or featureset that I want to work on using the [grill-me](.claude/skills/grill-me/SKILL.md) skill.
2. Create and review a PRD with [create-prd](.claude/skills/create-prd/SKILL.md) to come up with requirements for the product slice.
3. Convert the items into issues for my GitHub environment with the [create-backlog](.claude/skills/create-backlog/SKILL.md) skill.
4. After this I process each issue one-by-one 
  1. Use the [spec](.claude/skills/spec/SKILL.md) to work on the implementation plan for the issue.
  2. Implement the plan with the agent as normal.
  3. Review manually.

### Reviewing documents

After working with AI for a while I find it useful to review with the Claude
Code plugin in VSCode. It lets me select text and make comments on the content
of a document. VSCode will automatically pass on the selection to Claude Code
with my comments and accurately fix the issue. It even shows a diff before
editing if you choose the "Ask me before editing" mode.

### Working with agents

I've discovered that working with the workflow as described above doesn't
require involvement of a lot of agents. I'm not sure if this ever changes, but
for now I'm happy to say that I'm a single agent person.

### Why I prefer manual reviewing

I tried many times to build a review workflow with AI. And it caused so many
headaches. I wrote a couple of posts about this topic:

- [AI writes faster than we can review — here's how we fixed that](https://www.beyondautocomplete.nl/ai-writes-faster-than-we-can-review-heres-how-we-fixed-that/)
- [The long road to smarter code reviews with AI: making it measurable](https://www.beyondautocomplete.nl/the-long-road-to-smarter-code-reviews-with-ai-making-it-measurable/)

Conclusion to this topic so far is, it's better to make things smaller. It's
just too dangerous to leave review up to the AI because:

- The amount of code it has to review is too much to say anything smart about
  it.
- Smaller deployments always lead to less risk in production anyway.
