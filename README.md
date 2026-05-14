# /goal Starter Kit

A three-file template for building complete projects with Claude Code's `/goal` command. Fill in your project details, paste a goal command, and Claude builds the whole thing without you prompting every step.

## What `/goal` Does

Claude Code 2.1.139 shipped `/goal` on May 12, 2026. It lets you set a completion condition and Claude keeps working across turns until a separate evaluator model confirms the condition is met. The model doing the work is not the model deciding if the work is done.

Without it, Claude works one turn, stops, and waits for you to tell it to continue. You become the bottleneck.

## What's In Here

| File        | Purpose                                                                                                                                                                    |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `CLAUDE.md` | Project context template. Stack, directory structure, design direction, constraints, code style. Claude reads this automatically when you open a session in the directory. |
| `SPEC.md`   | Page-level requirements template. Sections, data schemas, interactive behavior. Includes inline guidance on writing specs that `/goal` can actually verify.                |
| `RUN.md`    | Workflow guide. Step-by-step setup, six goal templates for different project types, how to write good conditions, and troubleshooting.                                     |

## Quick Start

1. Clone this repo or copy the three files into a new project directory
2. Fill in `CLAUDE.md` with your stack and design direction
3. Fill in `SPEC.md` with your pages, components, and data schemas
4. Open Claude Code in the directory
5. Scaffold your project (`npx create-next-app`, `npm create astro`, whatever your stack needs)
6. Paste your `/goal` command (build it from the checklist at the bottom of SPEC.md)
7. Turn on auto mode
8. Do something else

## Goal Templates

RUN.md includes copy-paste goal templates for:

- **Static websites** (Next.js, Astro, SvelteKit)
- **Component libraries** (with Storybook)
- **APIs and backends**
- **Full-stack apps**
- **Refactors and migrations**
- **Bug bashes**

## The One Thing to Remember

Every condition in your `/goal` command must be provable from terminal output. The evaluator reads the conversation transcript, not your filesystem. "npm run build exits 0" works. "The site looks good" doesn't.

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) 2.1.139 or later
- A Claude Pro, Max, or Team plan

## About Wil

Built by [Wil Waldon](https://wilwaldon.com). I run [Frontier AI Labs](https://www.youtube.com/@FrontierAILabs) on YouTube and a community of the same name on Skool, focused on using Claude and AI tools to start and grow businesses. 1,700+ hours logged in Claude Code.

## License

MIT
