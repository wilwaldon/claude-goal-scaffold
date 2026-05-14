# Project: [YOUR PROJECT NAME]

[One sentence. What is this and who is it for.]

## Stack

- [Framework and version, e.g., Next.js 14 (App Router), Astro 4, SvelteKit 2]
- [Language, e.g., TypeScript]
- [Styling, e.g., Tailwind CSS]
- [Data layer, e.g., No database / Supabase / Firebase / JSON files]
- [Other deps worth mentioning. If Claude needs to install something specific, say so here.]

## Structure

```
src/
  [Map out your directory tree. Be specific. Claude will follow this exactly.]
  [If you skip this, Claude picks its own structure and you spend turns correcting it.]
public/
  [Static assets, images, fonts]
```

## Design Direction

[This is where most people underspec. Give Claude a real creative brief, not "make it look good."]

- Fonts: [Specific font pairings. Display + body. Pull from Google Fonts.]
- Palette: [3-5 colors with actual purpose. Background, text, primary, accent.]
- Layout: [Dense or spacious. Symmetric or asymmetric. Grid or freeform.]
- Mood: [What should someone feel when they land on this site? One sentence.]
- Anti-references: [What you do NOT want. "No corporate SaaS look." "No purple gradients." Be direct.]

## Content Source

[Where does page content come from? JSON files, markdown, hardcoded, CMS, API?]
[If JSON, specify the directory. If API, specify endpoints. If hardcoded, say so and own it.]

## Constraints

[List the hard boundaries. These prevent Claude from going off-script.]
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
- [Your formatter/linter config, if relevant]
- [Import ordering preferences]
- [File naming conventions: kebab-case, PascalCase, etc.]
