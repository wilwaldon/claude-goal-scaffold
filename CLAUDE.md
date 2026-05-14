# Project: [YOUR PROJECT NAME]

[One sentence. What is this and who is it for.]

## Stack

- [Framework and version, e.g., Next.js 14 (App Router), Astro 4, SvelteKit 2]
- [Language, e.g., TypeScript]
- [Styling, e.g., Tailwind CSS]
- [Data layer, e.g., No database / Supabase / Firebase / JSON files]
- [Other deps worth mentioning. If you need something specific installed, say so here.]

## Structure

```
src/
  [Map out your directory tree. Be specific. Claude will follow this exactly.]
  [If you skip this, Claude picks its own structure and you spend turns correcting it.]
public/
  [Static assets, images, fonts]
```

## Design Direction

[Give Claude a real creative brief, not "make it look good."]

- Fonts: [Specific font pairings. Display + body. Pull from Google Fonts.]
- Palette: [3-5 colors with actual purpose. Background, text, primary, accent.]
- Layout: [Dense or spacious. Symmetric or asymmetric. Grid or freeform.]
- Mood: [What should someone feel when they land on this? One sentence.]
- Anti-references: [What you do NOT want. Be direct.]

## Content Source

[Where does page content come from? JSON files, markdown, hardcoded, CMS, API?]
[If JSON, specify the directory. If API, specify endpoints. If hardcoded, say so and own it.]

## Constraints

[Hard boundaries. These prevent Claude from going off-script.]
[Examples:]

- No external API calls
- No authentication
- Fully responsive, mobile-first
- All pages must have working nav
- Semantic HTML, accessible markup
- No placeholder "lorem ipsum" text anywhere

## Code Style

[Your rules. Claude follows these for every file it writes.]
[Examples:]

- Functional components only
- Named exports for components, default exports for pages
- No `any` types
- [Formatter/linter config]
- [Import ordering preferences]
- [File naming conventions: kebab-case, PascalCase, etc.]

---

## Behavioral Rules

These apply to every task in this project. They bias toward caution over speed. For trivial tasks, use judgment.

### Think Before Coding

Don't assume. Don't hide confusion. Surface tradeoffs.

- State assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them. Don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

### Simplicity First

Minimum code that solves the problem. Nothing speculative.

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

The check: would a senior engineer say this is overcomplicated? If yes, simplify.

### Surgical Changes

Touch only what you must. Clean up only your own mess.

When editing existing code:

- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it. Don't delete it.

When your changes create orphans:

- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: every changed line should trace directly to the request.

### Goal-Driven Execution

Define success criteria. Loop until verified.

Transform every task into something verifiable:

- "Add validation" becomes "write tests for invalid inputs, then make them pass"
- "Fix the bug" becomes "write a test that reproduces it, then make it pass"
- "Refactor X" becomes "ensure tests pass before and after"

For multi-step tasks, state a brief plan:

```
1. [Step] -> verify: [check]
2. [Step] -> verify: [check]
3. [Step] -> verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

---

These behavioral rules are working if: diffs contain fewer unnecessary changes, rewrites from overcomplication go down, and clarifying questions come before implementation rather than after mistakes.
