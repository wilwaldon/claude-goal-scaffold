# /goal Starter Kit

## What This Is

Three files that turn Claude Code's `/goal` command into a hands-off project builder. Fill in CLAUDE.md and SPEC.md with your project details, paste a goal command, and let Claude build the whole thing while you do something else.

## The Files

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Project context. Stack, structure, design, constraints. Claude reads this automatically at session start. |
| `SPEC.md` | Page-level requirements. Every section, every data file, every behavior. |
| `RUN.md` | This file. Workflow instructions and goal templates. |

## Setup

1. Create a new directory for your project
2. Copy all three files into it
3. Fill in CLAUDE.md with your stack and design direction
4. Fill in SPEC.md with your pages and data schemas
5. Open Claude Code in that directory

## Step 1: Scaffold

Tell Claude to init the project:

```
Initialize a [framework] project with [language] and [styling] in this directory.
Use [router/config]. Read SPEC.md for the full site requirements.
```

Wait for the scaffold to finish. You want a working `npm run dev` before you set the goal.

## Step 2: Set the Goal

Paste your goal command. Build it from the checklist at the bottom of your SPEC.md.

The syntax:

```
/goal "[condition 1]. [condition 2]. [condition 3]."
```

Every condition must be something Claude can prove from its own terminal output. The evaluator reads the conversation transcript, not the filesystem. So "npm run build exits 0" works because Claude runs the build and the output shows in the conversation. "The design looks good" doesn't work because no command can prove that.

## Step 3: Auto Mode

Turn on auto mode so Claude doesn't stop to ask permission for every file write and command execution. Two separate systems working together:

- `/goal` keeps Claude working across turns
- Auto mode keeps Claude working within each turn

Without auto mode, Claude will pause every time it wants to run a command or write a file, and you're back to babysitting.

## Step 4: Walk Away

Claude will loop: write code, run builds, hit errors, fix them, rerun. The evaluator checks the goal condition after each turn. When every condition holds, the goal clears and Claude stops.

Run `/goal` with no arguments at any point to see elapsed time, turns, and tokens spent.

Run `/goal clear` to kill it early.

---

## Goal Templates

Copy, edit, paste. Replace the bracketed parts.

### Static Website (Next.js, Astro, etc.)

```
/goal "All [N] pages defined in SPEC.md are implemented at their defined routes. All data files in src/data/ exist with realistic sample content. Navigation works between all pages. [Interactive feature] works as specified. npm run build exits 0 with no TypeScript errors. npm run dev starts without errors."
```

### Component Library

```
/goal "All [N] components defined in SPEC.md are implemented and exported from src/components/index.ts. Each component has a corresponding story in [storybook/stories directory]. npm run build exits 0. npm run storybook starts without errors."
```

### API / Backend

```
/goal "All [N] endpoints defined in SPEC.md are implemented. Each endpoint returns the correct status code and response shape as specified. npm test exits 0 with all tests passing. npm run dev starts the server without errors."
```

### Full-Stack App

```
/goal "All [N] pages render at their defined routes. All [N] API endpoints return correct responses. Database migrations run without errors. npm run build exits 0. npm run dev starts both client and server without errors. npm test exits 0."
```

### Refactor / Migration

```
/goal "All instances of [old pattern/API/dependency] are replaced with [new pattern/API/dependency]. No files outside [scope directory] are modified. npm run build exits 0. npm test exits 0 with no regressions."
```

### Bug Bash

```
/goal "All [N] issues labeled [label] in [issue file/list] are resolved. Each fix includes a corresponding test. npm test exits 0. No unrelated files are modified."
```

---

## Writing Good Conditions

The goal condition can be up to 4,000 characters. Use all of it if you need to.

### Three Parts of a Strong Condition

1. **End state**: What exists when it's done. "All 5 pages render." "All tests pass." "The migration is complete."
2. **Proof**: How Claude demonstrates it. "npm run build exits 0." "npm test shows 24/24 passing." "git diff shows no remaining instances of the old API."
3. **Guardrails**: What Claude must not touch. "No files outside src/ are modified." "The database schema is unchanged." "No new dependencies are added."

### Common Mistakes

**Too vague:**
```
/goal "Build the website from the spec."
```
The evaluator can't determine what "built" means. Claude will do some work and the evaluator will shrug.

**No proof mechanism:**
```
/goal "All pages look correct and match the design."
```
No command produces output that proves visual correctness. The evaluator reads the transcript, not your screen.

**Missing guardrails:**
```
/goal "Migrate all API calls to the new SDK."
```
Claude might rewrite your test fixtures, config files, or documentation along the way. Add boundaries.

**Good:**
```
/goal "All API calls in src/services/ use @new-sdk/client instead of old-sdk. No files outside src/services/ are modified. npm run build exits 0. npm test exits 0 with no test failures."
```

---

## When It Gets Stuck

If Claude loops without making progress:

- `/goal clear` to kill the current goal
- Review what it built so far
- Narrow the scope. Break one big goal into 2-3 smaller sequential goals.
- Check if your condition is actually provable from terminal output

If the evaluator keeps saying the goal isn't met when you think it is:

- Your condition might be ambiguous. Rewrite it with more specific proof.
- The evaluator reads the transcript, not the filesystem. If Claude didn't run the verification command recently, the evaluator might not see the proof. Add explicit verification steps to your condition: "Run npm test and confirm 0 failures."
